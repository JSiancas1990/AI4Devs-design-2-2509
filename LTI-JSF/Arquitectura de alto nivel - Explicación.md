# Arquitectura de Alto Nivel - Sistema LTI ATS

## Resumen Ejecutivo

El sistema LTI utiliza una **arquitectura monolítica modular con procesamiento asíncrono separado**, diseñada para despliegue on-premise. Esta arquitectura balancea simplicidad operacional con capacidad de escalamiento donde más importa: el procesamiento de inteligencia artificial.

---

## Componentes Principales

### 1. Cliente - React Web Application

**Tecnología:** React  
**Función:** Interfaz de usuario para reclutadores

- Aplicación web de página única (SPA)
- Comunicación con el backend vía API REST
- Interfaz intuitiva para gestión de candidatos, ofertas y filtrado inteligente

---

### 2. Servidor de Aplicación - Monolito Modular

**Tecnología:** Node.js + Express + Prisma ORM  
**Puerto:** 4000  
**Función:** Lógica de negocio centralizada

#### Módulos Internos:
- **Gestión de Candidatos:** CRUD completo, experiencia laboral, formación (CU-01)
- **Gestión de Ofertas:** Creación y publicación de vacantes (CU-02)
- **Gestión de Aplicaciones:** Tracking de aplicaciones de candidatos
- **Integración con Portales:** Publicación automática en LinkedIn, Indeed, etc.
- **Autenticación y Auditoría:** JWT, RBAC, trazabilidad de cambios

#### Características:
- Módulos internos bien delimitados pero compartiendo proceso
- Prisma ORM para acceso eficiente a datos
- API REST para comunicación con frontend
- Logging estructurado y manejo centralizado de errores

---

### 3. Procesamiento Asíncrono

#### Message Queue
**Tecnología:** Redis o RabbitMQ  
**Función:** Cola de mensajes para tareas pesadas

- Desacopla el procesamiento intensivo del flujo principal
- Garantiza procesamiento confiable de tareas
- Permite reintento de tareas fallidas

#### AI Workers
**Tecnología:** Python + Celery + spaCy  
**Función:** Procesamiento inteligente de candidatos (CU-03)

##### Capacidades:
- **Análisis de CVs:** Extracción de información mediante NLP
- **Filtrado Inteligente:** Matching semántico de candidatos con ofertas
- **Scoring Automático:** Cálculo de compatibilidad 0-100
- **Escalabilidad Horizontal:** Múltiples workers según demanda

##### Ventajas:
- No bloquea operaciones CRUD del monolito
- Cumple SLA de 30 segundos para 100 candidatos
- Procesamiento en paralelo de múltiples solicitudes

---

### 4. Capa de Datos

#### PostgreSQL 15+
**Función:** Base de datos relacional principal

- Almacenamiento de candidatos, ofertas, aplicaciones, usuarios
- Transacciones ACID para integridad de datos
- Réplica para alta disponibilidad (read-only)
- Schemas lógicos por módulo

#### Redis Cache
**Función:** Cache en memoria

- Almacenamiento de sesiones de usuario
- Cache de consultas frecuentes
- Mejora tiempos de respuesta hasta 10x

#### MinIO
**Función:** Almacenamiento de objetos (S3-compatible)

- Almacenamiento de CVs (PDF, DOC, DOCX)
- Documentos de candidatos (certificados, cartas)
- Encriptación de archivos sensibles
- Versionado de documentos

---

### 5. Servicios Externos

**Portales de Empleo Integrados:**
- LinkedIn Jobs
- Indeed
- CompuTrabajo
- Bumeran

**Función:** Publicación multi-canal de ofertas laborales

- Integración vía APIs REST
- Sincronización automática de estados
- Tracking de visualizaciones y clics

---

### 6. Observabilidad

**Tecnologías:** Prometheus + Grafana

#### Prometheus
- Recolección de métricas en tiempo real
- Alertas automáticas por umbrales
- Monitoreo de disponibilidad de servicios

#### Grafana
- Dashboards visuales de métricas
- Análisis de performance
- Logs centralizados de aplicación

---

## Flujos de Datos Principales

### Flujo Síncrono (Operaciones CRUD)

```
React → Backend → Prisma → PostgreSQL
                 ↓
              Redis Cache
                 ↓
              MinIO (archivos)
```

**Casos de uso:** Consultar candidatos, crear ofertas, ver aplicaciones

---

### Flujo Asíncrono (Procesamiento IA)

```
Backend → Message Queue → AI Workers → spaCy
                             ↓
                        PostgreSQL (resultados)
                             ↓
                        MinIO (lectura CVs)
```

**Casos de uso:** Filtrado inteligente de candidatos (CU-03)

**Proceso:**
1. Reclutador inicia filtrado desde UI
2. Backend encola tarea en Redis/RabbitMQ
3. Worker disponible consume tarea
4. Worker descarga CVs desde MinIO
5. spaCy procesa y analiza documentos
6. Worker calcula scoring de compatibilidad
7. Resultados se almacenan en PostgreSQL
8. UI muestra ranking de candidatos

---

### Flujo de Publicación en Portales

```
Backend → Portal Integration Module → APIs Externas
             ↓
        PostgreSQL (tracking)
```

**Proceso:**
1. Reclutador crea oferta y selecciona portales
2. Backend adapta formato según cada portal
3. Publicación vía API a portales externos
4. Registro de URLs y estados de publicación

---

## Ventajas de Esta Arquitectura

### ✅ Simplicidad Operacional
- Despliegue de 2 aplicaciones principales (monolito + workers)
- Menor complejidad que microservicios
- Debugging más sencillo

### ✅ Escalabilidad Selectiva
- Workers IA escalan horizontalmente según carga
- Monolito maneja bien operaciones CRUD estándar
- Cache Redis reduce carga en base de datos

### ✅ Resiliencia
- Fallo en workers IA no afecta consultas de candidatos
- Cola de mensajes garantiza procesamiento eventual
- Réplica de PostgreSQL para alta disponibilidad

### ✅ Performance
- Cache reduce latencia en consultas frecuentes
- Procesamiento asíncrono no bloquea UI
- MinIO optimizado para grandes archivos

### ✅ Mantenibilidad
- Módulos internos bien delimitados
- Separación clara de responsabilidades
- Fácil evolución a microservicios si es necesario

---

## Infraestructura Requerida (On-Premise)

### Configuración Mínima (MVP)

| Servidor | Propósito | Especificaciones |
|----------|-----------|------------------|
| **App Server** | Monolito Node.js | 4 cores, 16GB RAM |
| **Worker Server** | AI Workers Python | 8 cores, 32GB RAM |
| **Database Server** | PostgreSQL + Réplica | 8 cores, 32GB RAM |
| **Storage Server** | Redis + MinIO | 4 cores, 16GB RAM |

**Total:** ~4 servidores físicos o VMs

### Configuración Escalada (Producción)

| Servidor | Propósito | Especificaciones |
|----------|-----------|------------------|
| **Load Balancer** | Nginx | 2 cores, 4GB RAM |
| **App Servers (x2)** | Monolito Node.js | 4 cores, 16GB RAM c/u |
| **Worker Servers (x3)** | AI Workers Python | 8 cores, 32GB RAM c/u |
| **DB Primary** | PostgreSQL Master | 16 cores, 64GB RAM |
| **DB Replica** | PostgreSQL Slave | 16 cores, 64GB RAM |
| **Cache Server** | Redis Cluster | 8 cores, 32GB RAM |
| **Storage Server** | MinIO Distributed | 8 cores, 64GB RAM |
| **Monitoring** | Prometheus + Grafana | 4 cores, 16GB RAM |

**Total:** ~11 servidores

---

## Stack Tecnológico Completo

### Frontend
- React 18+
- TypeScript
- Tailwind CSS
- React Query (data fetching)

### Backend
- Node.js 20 LTS
- Express.js
- Prisma ORM
- TypeScript

### AI Processing
- Python 3.11+
- Celery (task queue)
- spaCy (NLP)
- Transformers (modelos avanzados)

### Infraestructura
- PostgreSQL 15+
- Redis 7+
- MinIO (latest)
- RabbitMQ (alternativa a Redis)

### DevOps
- Docker + Docker Compose
- Nginx (reverse proxy)
- Prometheus (métricas)
- Grafana (visualización)
- Winston/Pino (logging)

---

## Consideraciones de Seguridad

- ✅ **Autenticación:** JWT con refresh tokens
- ✅ **Autorización:** RBAC (Role-Based Access Control)
- ✅ **Encriptación:** TLS/SSL en tránsito, AES-256 en reposo
- ✅ **Protección de Datos:** Cumplimiento GDPR y LOPD
- ✅ **Auditoría:** Logs completos de operaciones sensibles
- ✅ **Rate Limiting:** Protección contra ataques de fuerza bruta

---

## Roadmap de Evolución

### Fase 1: MVP (Actual)
- Monolito modular + 1 AI Worker
- Funcionalidades básicas CU-01, CU-02, CU-03

### Fase 2: Optimización
- Agregar 2-3 workers adicionales
- Implementar cache avanzado
- Optimización de queries

### Fase 3: Alta Disponibilidad
- Load balancer
- Réplicas de PostgreSQL
- Redis cluster

### Fase 4: Microservicios (Si se justifica)
- Extraer Portal Integration Service
- Extraer Document Management Service
- Mantener core como monolito

---

## Conclusión

Esta arquitectura proporciona un **balance óptimo entre simplicidad y capacidad** para un sistema ATS en fase MVP con despliegue on-premise. La separación del procesamiento IA mediante workers asegura que el análisis intensivo no degrada la experiencia de usuario en operaciones cotidianas, mientras mantiene la simplicidad operacional de un monolito bien estructurado.

La arquitectura está preparada para crecer orgánicamente: primero escalando horizontalmente los workers, luego agregando réplicas del monolito, y finalmente evolucionando a microservicios solo si el negocio lo justifica.