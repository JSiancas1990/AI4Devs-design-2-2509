# Documento Consolidado del MVP para el sistema LTI

## Índice

1. [Historias de Usuario](#1-historias-de-usuario)
2. [Product Backlog](#2-product-backlog)
3. [Tickets de Trabajo - US-001](#3-tickets-de-trabajo---us-001)

***

## 1. Historias de Usuario

# Historias de Usuario - LTI
## Versión 3.0

---

## Épica 1: Gestión de Candidatos

### US-001: Crear perfil básico de candidato
**Como** Reclutador  
**Quiero** crear un perfil de candidato con datos personales básicos  
**Para** comenzar a construir mi base de datos de talento

**Criterios de Aceptación:**
- Puedo ingresar nombre completo, email, teléfono y ubicación (ciudad, país)
- Puedo ingresar enlaces profesionales opcionales: LinkedIn URL, Portafolio web URL
- Puedo especificar disponibilidad: Disponible Inmediatamente, No Disponible, Disponible desde [fecha futura]
- El valor por defecto de disponibilidad es "Disponible Inmediatamente"
- El sistema valida que el email no esté duplicado (email único)
- El sistema valida formato de email (ejemplo@dominio.com)
- El sistema valida formato de teléfono internacional (acepta +, -, espacios, paréntesis, números)
- El sistema valida formato URL para LinkedIn y portafolio (opcional, pero si se llena debe ser URL válida)
- Recibo confirmación visual al crear el perfil exitosamente

**Historias de Usuario Relacionadas:** US-030

**Estimación:** 5 puntos  
**Prioridad:** Alta

---

### US-002: Agregar experiencia laboral a candidato
**Como** Reclutador  
**Quiero** registrar la experiencia laboral del candidato  
**Para** conocer su trayectoria profesional

**Criterios de Aceptación:**
- Puedo agregar múltiples experiencias laborales al mismo candidato
- Cada experiencia incluye: empresa, cargo, fechas (inicio y fin), responsabilidades (texto largo, múltiples líneas)
- Puedo marcar si es el trabajo actual (checkbox "Trabajo actual")
- Si marco "Trabajo actual", el campo fecha de fin queda deshabilitado
- El sistema valida que la fecha de inicio sea anterior a la fecha de fin (si fecha fin existe)
- Puedo editar todos los campos o eliminar experiencias ya agregadas

**Historias de Usuario Relacionadas:** US-001, US-030

**Estimación:** 5 puntos  
**Prioridad:** Alta

---

### US-003: Agregar formación académica y certificaciones a candidato
**Como** Reclutador  
**Quiero** registrar la formación académica y certificaciones del candidato  
**Para** validar su nivel educativo y credenciales profesionales

**Criterios de Aceptación:**
- **Formación Académica:**
  - Puedo agregar múltiples formaciones académicas al mismo candidato
  - Cada formación incluye: institución, título, área de estudio, año de graduación
  - Puedo especificar el nivel educativo: Secundaria, Técnico, Universitario (Licenciatura), Posgrado (Maestría), Posgrado (Doctorado)
- **Certificaciones:**
  - Puedo agregar múltiples certificaciones al mismo candidato
  - Cada certificación incluye: nombre, institución emisora, fecha de obtención, fecha de expiración (opcional)
- Puedo editar todos los campos o eliminar formaciones y certificaciones ya agregadas

**Historias de Usuario Relacionadas:** US-001, US-030

**Estimación:** 5 puntos  
**Prioridad:** Alta

---

### US-004: Agregar habilidades e idiomas a candidato
**Como** Reclutador  
**Quiero** registrar las habilidades e idiomas del candidato  
**Para** identificar sus competencias técnicas, blandas y capacidades de comunicación

**Criterios de Aceptación:**
- **Habilidades:**
  - Puedo agregar múltiples habilidades al mismo candidato
  - Puedo categorizar cada habilidad como: Técnica o Blanda
  - Puedo especificar nivel de dominio: Básico, Intermedio, Avanzado, Experto
  - Puedo indicar años de experiencia con cada habilidad (número entero)
  - Puedo seleccionar habilidades del catálogo existente o crear nuevas
- **Idiomas:**
  - Puedo agregar múltiples idiomas al mismo candidato
  - Cada idioma incluye: nombre del idioma, nivel de dominio (Básico, Intermedio, Avanzado, Nativo)
  - Puedo especificar si tiene certificación oficial (ej: TOEFL, IELTS, DELE)
- Puedo editar todos los campos o eliminar habilidades e idiomas ya agregados

**Historias de Usuario Relacionadas:** US-001, US-034, US-030

**Estimación:** 8 puntos  
**Prioridad:** Alta

---

### US-005: Adjuntar documentos a perfil de candidato
**Como** Reclutador  
**Quiero** subir el CV y otros documentos del candidato  
**Para** tener toda su información en un solo lugar

**Criterios de Aceptación:**
- Puedo subir archivos en formato PDF, DOC, DOCX, JPG, PNG
- El tamaño máximo por archivo es 10 MB
- Puedo identificar el tipo de documento: CV/Resume, Certificado, Carta de Presentación, Diploma, Portafolio, Otro
- Si selecciono "Otro", puedo agregar descripción personalizada del documento
- Los documentos quedan vinculados al perfil del candidato
- Puedo descargar los documentos previamente subidos
- Puedo eliminar documentos obsoletos
- El sistema muestra: nombre del archivo, tipo, tamaño, fecha de subida y usuario que lo subió

**Historias de Usuario Relacionadas:** US-001, US-030

**Estimación:** 8 puntos  
**Prioridad:** Alta

---

### US-006: Buscar candidatos por criterios básicos
**Como** Reclutador  
**Quiero** buscar candidatos usando filtros simples  
**Para** encontrar perfiles específicos rápidamente

**Criterios de Aceptación:**
- Puedo buscar por nombre del candidato (búsqueda parcial, case-insensitive)
- Puedo filtrar por ubicación (ciudad, país)
- Puedo filtrar por disponibilidad: Disponible Inmediatamente, No Disponible, Disponible desde [fecha futura]
- Puedo combinar múltiples filtros simultáneamente (operador AND)
- Veo resultados en menos de 2 segundos para hasta 10,000 perfiles
- Los resultados muestran información resumida: nombre, email, ubicación, disponibilidad
- Si no hay resultados, veo mensaje "No se encontraron candidatos con los criterios especificados"

**Historias de Usuario Relacionadas:** US-001, US-030

**Estimación:** 5 puntos  
**Prioridad:** Alta

---

### US-007: Buscar candidatos por habilidades e idiomas
**Como** Reclutador  
**Quiero** buscar candidatos que tengan habilidades e idiomas específicos  
**Para** encontrar el talento adecuado para mis vacantes

**Criterios de Aceptación:**
- Puedo buscar por una o múltiples habilidades simultáneamente
- Puedo especificar nivel de dominio requerido: Básico, Intermedio, Avanzado, Experto
- Puedo especificar años mínimos de experiencia con la habilidad
- Puedo buscar por uno o múltiples idiomas simultáneamente
- Puedo especificar nivel de idioma requerido: Básico, Intermedio, Avanzado, Nativo
- Veo resultados que coinciden con TODOS los criterios especificados (operador AND)
- Los resultados muestran qué habilidades e idiomas tiene cada candidato con sus niveles

**Historias de Usuario Relacionadas:** US-001, US-004, US-030

**Estimación:** 5 puntos  
**Prioridad:** Media

---

### US-008: Ver detalle completo de candidato
**Como** Reclutador  
**Quiero** ver toda la información de un candidato en una sola vista  
**Para** evaluar su perfil completo

**Criterios de Aceptación:**
- Veo datos personales: nombre, email, teléfono, ubicación
- Veo enlaces profesionales: LinkedIn, portafolio. Si no existen, se muestran vacíos.
- Veo disponibilidad actual del candidato
- Veo toda la experiencia laboral ordenada cronológicamente (más reciente primero)
- Veo toda la formación académica y certificaciones ordenadas por fecha
- Veo todas las habilidades organizadas por categoría (Técnicas / Blandas)
- Veo todos los idiomas con sus niveles de dominio
- Puedo descargar todos los documentos adjuntos
- La información se carga en menos de 1 segundo

**Historias de Usuario Relacionadas:** US-001, US-002, US-003, US-004, US-005, US-030

**Estimación:** 3 puntos  
**Prioridad:** Alta

---

### US-009: Actualizar información de candidato
**Como** Reclutador  
**Quiero** editar la información de un candidato existente  
**Para** mantener los datos actualizados

**Criterios de Aceptación:**
- Puedo modificar cualquier campo del perfil: datos personales, disponibilidad, enlaces, experiencia, formación, certificaciones, habilidades, idiomas
- El sistema me muestra los datos actuales pre-cargados en el formulario
- El sistema aplica las mismas validaciones que al crear el perfil
- Recibo confirmación de actualización exitosa
- La actualización queda registrada en el historial de cambios con: fecha, hora, usuario y campos modificados (valores anteriores vs nuevos)

**Historias de Usuario Relacionadas:** US-001, US-011, US-030

**Estimación:** 5 puntos  
**Prioridad:** Alta

---

### US-010: Eliminar perfil de candidato
**Como** Reclutador  
**Quiero** eliminar perfiles duplicados u obsoletos  
**Para** mantener mi base de datos limpia

**Criterios de Aceptación:**
- El sistema me solicita confirmación explícita antes de eliminar
- Veo un resumen del perfil a eliminar: nombre, email, fecha de registro
- No puedo eliminar candidatos que tienen aplicaciones en estado: Aplicado o En Revisión (solo puedo eliminar si todas sus aplicaciones están Rechazadas o Aceptadas, o no tiene aplicaciones)
- El perfil se elimina lógicamente (campo "eliminado" = true, no se borra físicamente de BD)
- Los documentos asociados se mantienen archivados por 90 días
- La eliminación queda registrada en el historial de cambios con fecha, hora y usuario
- El perfil eliminado ya no aparece en búsquedas ni listados (se filtra automáticamente)

**Historias de Usuario Relacionadas:** US-001, US-019, US-011, US-030

**Estimación:** 3 puntos  
**Prioridad:** Media

---

### US-011: Ver historial de cambios de candidato
**Como** Reclutador  
**Quiero** ver el historial de modificaciones de un perfil  
**Para** hacer seguimiento de actualizaciones y cumplir con auditoría (GDPR/LOPD)

**Criterios de Aceptación:**
- Veo fecha y hora de cada operación realizada sobre el perfil
- Veo nombre del usuario que realizó cada operación
- Veo tipo de operación: Crear, Actualizar, Eliminar
- Para operaciones "Actualizar", veo qué campos específicos fueron modificados con formato: "Campo: [valor anterior] → [valor nuevo]"
- Puedo filtrar por tipo de operación: Crear, Actualizar, Eliminar (checkbox múltiple)
- Puedo filtrar por rango de fechas (fecha inicio - fecha fin)
- El historial está ordenado cronológicamente (más reciente primero)
- El historial se mantiene por al menos 2 años para cumplimiento normativo

**Historias de Usuario Relacionadas:** US-001, US-009, US-010, US-030

**Estimación:** 5 puntos  
**Prioridad:** Baja

---

## Épica 2: Publicación de Ofertas Laborales

### US-012: Crear oferta laboral completa
**Como** Reclutador  
**Quiero** crear una nueva oferta de trabajo con todos sus detalles  
**Para** iniciar un proceso de reclutamiento

**Criterios de Aceptación:**
- **Información básica (obligatoria):**
  - Título del puesto
  - Departamento (ej: Tecnología, Ventas, Marketing, RRHH, Operaciones, Finanzas, Otro)
  - Descripción del puesto (texto largo)
  - Requisitos obligatorios (texto largo)
  - Requisitos deseables (texto largo, opcional)
- **Detalles del puesto (obligatorios):**
  - Ubicación (ciudad, país) o checkbox "100% Remoto"
  - Modalidad de trabajo: Presencial, Híbrido, Remoto
  - Tipo de contrato: Tiempo Completo, Medio Tiempo, Por Proyecto, Prácticas/Pasantía
  - Número de vacantes (número entero, mínimo 1)
- **Fechas:**
  - Fecha de inicio deseada (opcional)
  - Fecha límite de aplicación (opcional, si se especifica debe ser fecha futura)
- **Compensación y beneficios:**
  - Rango salarial: salario mínimo y salario máximo (números decimales)
  - Moneda: USD, EUR, PEN, MXN, ARS, COP, CLP
  - Visibilidad salarial: Público (candidatos ven el rango), Privado (candidatos no ven el rango)
  - Beneficios ofrecidos (texto libre): seguro médico, bonos, vacaciones, etc.
- **Configuración:**
  - Visibilidad de la oferta: Pública (cualquier candidato puede aplicar), Privada (solo candidatos invitados)
- **Validaciones:**
  - El sistema valida campos obligatorios
  - El sistema valida que salario máximo sea mayor o igual al mínimo
  - El sistema valida que fecha límite sea posterior a hoy
- La oferta queda guardada con estado "Borrador"

**Historias de Usuario Relacionadas:** US-030

**Estimación:** 8 puntos  
**Prioridad:** Alta

---

### US-013: Publicar oferta en múltiples portales
**Como** Reclutador  
**Quiero** publicar una oferta en varios portales simultáneamente  
**Para** maximizar el alcance sin trabajo manual repetitivo

**Criterios de Aceptación:**
- Puedo seleccionar uno o más portales: LinkedIn, Indeed, CompuTrabajo (checkboxes)
- Solo puedo publicar si la oferta está completa (todos los campos obligatorios llenos)
- La publicación se ejecuta con un solo clic en botón "Publicar en portales seleccionados"
- El sistema adapta automáticamente el formato de la oferta según requisitos de cada portal
- Veo indicador de progreso mientras se publican las ofertas
- Recibo resumen de resultados: "Publicada exitosamente en X de Y portales"
- Si un portal falla, los demás continúan su proceso (fallos independientes)
- El estado de la oferta cambia de "Borrador" a "Publicada" cuando al menos un portal es exitoso
- El proceso completo toma menos de 5 minutos para 3 portales
- Cada publicación exitosa registra: URL de publicación, ID externo del portal, fecha y hora

**Historias de Usuario Relacionadas:** US-012, US-033, US-030

**Estimación:** 13 puntos  
**Prioridad:** Alta

---

### US-014: Ver estado de publicación por portal
**Como** Reclutador  
**Quiero** consultar el estado de mis ofertas en cada portal  
**Para** verificar que estén activas correctamente

**Criterios de Aceptación:**
- Veo estado por cada portal seleccionado: Exitosa (verde), Pendiente (amarillo), Fallida (rojo)
- Para publicaciones exitosas, veo:
  - URL de la publicación en el portal externo (link clicable que abre en nueva pestaña)
  - Fecha y hora de publicación
  - Fecha de expiración (si el portal la proporciona)
  - ID externo de la publicación
- Para publicaciones fallidas, veo mensaje de error resumido
- Puedo hacer clic en "Ver detalle de error" para ver logs completos

**Historias de Usuario Relacionadas:** US-013, US-015, US-030

**Estimación:** 5 puntos  
**Prioridad:** Alta

---

### US-015: Ver logs de errores de publicación
**Como** Reclutador  
**Quiero** revisar los errores de publicación fallida  
**Para** entender qué salió mal y poder reportar o corregir

**Criterios de Aceptación:**
- Veo detalle del error por cada portal que falló
- Veo tipo de error clasificado: Error de Credenciales, Error de Formato, Error de Conexión, Error Desconocido
- Veo mensaje de error específico (retornado por la API del portal)
- Veo timestamp completo del intento de publicación (día/mes/año hora:minuto:segundo)
- Veo request y response técnico (solo para usuarios Admin, útil para debugging)
- Los logs quedan guardados permanentemente para consulta posterior
- Veo historial de todos los intentos de publicación (incluyendo reintentos)

**Historias de Usuario Relacionadas:** US-013, US-014, US-030

**Estimación:** 5 puntos  
**Prioridad:** Media

---

### US-016: Consultar ofertas activas
**Como** Reclutador  
**Quiero** ver un listado de todas mis ofertas  
**Para** gestionar mis procesos de reclutamiento en curso

**Criterios de Aceptación:**
- Veo listado con: título del puesto, departamento, fecha de publicación, número de aplicaciones recibidas, estado
- Puedo filtrar por estado: Borrador, Publicada, Pausada, Cerrada, Expirada
  - **Borrador**: oferta creada pero no publicada
  - **Publicada**: oferta activa en al menos un portal
  - **Pausada**: oferta temporalmente desactivada (vacantes cubiertas temporalmente)
  - **Cerrada**: proceso finalizado, todas las vacantes cubiertas
  - **Expirada**: fecha límite de aplicación superada
- Puedo ordenar por: Fecha de creación (más reciente/antigua), Número de aplicaciones (mayor/menor)
- Puedo buscar por título del puesto o departamento (búsqueda parcial)
- Puedo acceder al detalle de cada oferta haciendo clic en la fila

**Historias de Usuario Relacionadas:** US-012, US-013, US-030

**Estimación:** 5 puntos  
**Prioridad:** Media

---

### US-017: Ver detalle completo de oferta
**Como** Reclutador  
**Quiero** ver toda la información de una oferta publicada  
**Para** revisar los detalles y estado actual

**Criterios de Aceptación:**
- Veo toda la información de la oferta: título, departamento, descripción, requisitos, beneficios, salario, ubicación, modalidad, tipo de contrato
- Veo fechas: fecha de creación, fecha de publicación, fecha de inicio deseada, fecha límite
- Veo número de vacantes totales y vacantes restantes (totales - aceptadas)
- Veo estado actual de la oferta: Borrador, Publicada, Pausada, Cerrada, Expirada
- Veo estado de publicación en cada portal (tabla con: portal, estado, URL, fecha)
- Veo número total de candidatos aplicados con desglose por estado: Aplicado, En Revisión, Rechazado, Aceptado
- Puedo acceder a la lista de candidatos aplicados desde esta vista (botón "Ver aplicaciones")

**Historias de Usuario Relacionadas:** US-012, US-014, US-018, US-030

**Estimación:** 3 puntos  
**Prioridad:** Media

---

## Épica 3: Gestión de Aplicaciones

### US-018: Ver candidatos aplicados a oferta
**Como** Reclutador  
**Quiero** ver qué candidatos han aplicado a cada oferta  
**Para** comenzar el proceso de evaluación

**Criterios de Aceptación:**
- Veo lista de candidatos con información resumida: nombre, email, ubicación, experiencia (años)
- Veo fecha de aplicación completa (día/mes/año hora:minuto)
- Veo fuente de aplicación: LinkedIn, Indeed, CompuTrabajo, Manual (si el reclutador asoció manualmente)
- Veo estado actual de cada aplicación: Aplicado, En Revisión, Rechazado, Aceptado
- Puedo ordenar por fecha de aplicación (más reciente/antigua) o por estado
- Puedo filtrar por estado de aplicación (checkboxes múltiples)
- Puedo filtrar por fuente de aplicación
- Puedo acceder al perfil completo de cada candidato haciendo clic en su nombre
- Si no hay aplicaciones, veo mensaje "Aún no hay candidatos aplicados a esta oferta"

**Historias de Usuario Relacionadas:** US-012, US-013, US-008, US-030

**Estimación:** 5 puntos  
**Prioridad:** Alta

---

### US-019: Cambiar estado de aplicación
**Como** Reclutador  
**Quiero** actualizar el estado de cada aplicación  
**Para** hacer seguimiento del proceso de selección

**Criterios de Aceptación:**
- Puedo cambiar estado entre: Aplicado, En Revisión, Rechazado, Aceptado
- El cambio se realiza mediante dropdown o botones de acción rápida
- El cambio se refleja inmediatamente en el listado
- Si intento cambiar a "Aceptado" pero ya no hay vacantes disponibles, el sistema muestra advertencia: "No hay vacantes disponibles. Vacantes totales: X, Aceptadas: Y"
- Puedo ver el historial de cambios de estado: fecha, hora, usuario, estado anterior → estado nuevo
- El sistema me solicita confirmación antes de cambiar a "Rechazado" o "Aceptado"
- Al aceptar un candidato, el contador de "vacantes restantes" de la oferta se reduce en 1

**Historias de Usuario Relacionadas:** US-018, US-030

**Estimación:** 5 puntos  
**Prioridad:** Media

---

### US-020: Agregar notas a aplicación
**Como** Reclutador  
**Quiero** agregar notas y comentarios a cada aplicación  
**Para** registrar impresiones, feedback de entrevistas y decisiones

**Criterios de Aceptación:**
- Puedo escribir texto libre como nota (sin límite de caracteres)
- Las notas quedan vinculadas a la aplicación específica (candidato + oferta)
- Veo fecha, hora y usuario que escribió cada nota
- Puedo ver todas las notas en orden cronológico (más reciente primero)
- Puedo editar mis propias notas dentro de las primeras 24 horas
- Puedo eliminar mis propias notas
- Solo usuarios con rol Reclutador o Admin pueden ver notas (confidencialidad)
- Las notas no son visibles para el candidato

**Historias de Usuario Relacionadas:** US-018, US-030

**Estimación:** 3 puntos  
**Prioridad:** Baja

---

## Épica 4: Filtrado Inteligente con IA

### US-021: Definir criterios de filtrado para oferta
**Como** Reclutador  
**Quiero** especificar qué estoy buscando en candidatos para una oferta  
**Para** que el sistema me ayude a identificarlos mediante IA

**Criterios de Aceptación:**
- **Criterios básicos:**
  - Puedo ingresar palabras clave obligatorias (texto separado por comas, ej: "Python, Django, REST API")
  - Puedo especificar años de experiencia mínima total (número entero)
  - Puedo definir nivel educativo mínimo requerido: Secundaria, Técnico, Universitario, Posgrado (Maestría), Posgrado (Doctorado)
- **Habilidades requeridas:**
  - Puedo seleccionar múltiples habilidades del catálogo
  - Puedo marcar cada habilidad como: Obligatoria o Deseable
  - Puedo especificar nivel de dominio esperado por habilidad: Básico, Intermedio, Avanzado, Experto
  - Puedo especificar años mínimos de experiencia con cada habilidad
- **Idiomas requeridos:**
  - Puedo seleccionar múltiples idiomas
  - Puedo marcar cada idioma como: Obligatorio o Deseable
  - Puedo especificar nivel esperado: Básico, Intermedio, Avanzado, Nativo
- **Ponderaciones:**
  - Puedo asignar peso a cada categoría: Palabras Clave (%), Habilidades (%), Experiencia (%), Educación (%), Idiomas (%)
  - La suma de todos los porcentajes debe ser exactamente 100%
  - El sistema valida la suma y muestra error si no es 100%
  - Puedo usar botón "Distribución Equitativa" para asignar porcentajes iguales automáticamente
- Los criterios quedan guardados y vinculados a la oferta laboral
- Puedo guardar el criterio como plantilla reutilizable con un nombre (opcional)
- Puedo cargar plantillas previamente guardadas

**Historias de Usuario Relacionadas:** US-012, US-018, US-034, US-030

**Estimación:** 8 puntos  
**Prioridad:** Alta

---

### US-022: Ejecutar filtrado automático con IA
**Como** Reclutador  
**Quiero** activar el análisis inteligente de candidatos  
**Para** obtener una lista priorizada automáticamente

**Criterios de Aceptación:**
- Puedo iniciar el filtrado con un clic en botón "Ejecutar Filtrado IA" desde la vista de la oferta
- El sistema valida que existan criterios de filtrado definidos antes de ejecutar
- El sistema valida que existan candidatos aplicados (si no hay aplicaciones, muestra mensaje "No hay candidatos para filtrar")
- El sistema procesa todos los candidatos aplicados a la oferta mediante el Motor de IA
- Veo indicador de progreso con mensaje "Analizando candidatos..." mientras el análisis está en curso
- Veo estimación de tiempo basada en cantidad de candidatos: "Tiempo estimado: X segundos"
- Recibo notificación visual cuando el proceso termina: "Filtrado completado. X candidatos analizados"
- El análisis completa en menos de 30 segundos para hasta 100 candidatos
- Si hay más de 100 candidatos, el sistema procesa en lotes y actualiza el progreso
- El sistema registra en historial: fecha/hora de ejecución, usuario que ejecutó, número de candidatos procesados, tiempo de procesamiento

**Historias de Usuario Relacionadas:** US-021, US-018, US-030

**Estimación:** 13 puntos  
**Prioridad:** Alta

---

### US-023: Ver resultados de filtrado con scoring
**Como** Reclutador  
**Quiero** ver candidatos ordenados por compatibilidad  
**Para** enfocarme en los mejores matches primero

**Criterios de Aceptación:**
- Veo lista ordenada de candidatos por scoring descendente (100 a 0, mejores primero)
- Cada candidato muestra: nombre, email, scoring numérico (0-100), categoría de compatibilidad
- Las categorías son: Excelente (80-100, verde), Bueno (60-79, azul), Regular (40-59, amarillo), Bajo (0-39, rojo)
- Veo información resumida adicional: ubicación, años de experiencia, disponibilidad
- Puedo filtrar por rango de scoring (slider o inputs: scoring mínimo - máximo)
- Puedo filtrar por categoría (checkboxes: Excelente, Bueno, Regular, Bajo)
- Puedo acceder al perfil completo de cada candidato haciendo clic en su nombre
- Puedo ver la justificación detallada del scoring haciendo clic en "Ver análisis" (lleva a US-024)
- El scoring se valida que esté entre 0-100 (el Motor IA debe garantizarlo)

**Historias de Usuario Relacionadas:** US-022, US-008, US-024, US-030

**Estimación:** 5 puntos  
**Prioridad:** Alta

---

### US-024: Ver justificación detallada de scoring
**Como** Reclutador  
**Quiero** entender por qué un candidato obtuvo cierto puntaje  
**Para** validar la recomendación del sistema y tomar decisiones informadas

**Criterios de Aceptación:**
- Veo desglose del scoring total en scores parciales por cada criterio evaluado:
  - Palabras Clave: X puntos de Y posibles (Z%)
  - Habilidades: X puntos de Y posibles (Z%)
  - Experiencia: X puntos de Y posibles (Z%)
  - Educación: X puntos de Y posibles (Z%)
  - Idiomas: X puntos de Y posibles (Z%)
- Para cada criterio, veo justificación en lenguaje natural:
  - **Cumple:** lista de elementos que SÍ cumplió (ej: "Tiene Python nivel Avanzado con 5 años de experiencia")
  - **No cumple:** lista de elementos que NO cumplió (ej: "No tiene certificación en AWS requerida")
- Veo análisis semántico de palabras clave encontradas en el CV (destacadas)
- La explicación es clara y comprensible (lenguaje natural, sin jerga técnica)
- Puedo expandir/colapsar cada sección de justificación
- Puedo comparar las justificaciones de 2 candidatos lado a lado (opcional, pero útil)

**Historias de Usuario Relacionadas:** US-023, US-030

**Estimación:** 5 puntos  
**Prioridad:** Alta

---

### US-025: Ajustar criterios y re-ejecutar filtrado
**Como** Reclutador  
**Quiero** modificar los criterios de filtrado y volver a ejecutar  
**Para** afinar los resultados según mi juicio y experiencia

**Criterios de Aceptación:**
- Puedo editar cualquier criterio previamente definido: palabras clave, habilidades, experiencia, educación, idiomas, ponderaciones
- El sistema me muestra los criterios actuales pre-cargados
- Puedo re-ejecutar el filtrado sin perder el resultado anterior (se guarda en historial)
- Los resultados se actualizan con los nuevos criterios
- Veo indicador visual que dice "Resultados del filtrado anterior disponibles en historial"
- El sistema me pregunta: "¿Deseas guardar estos criterios modificados?" (botón Sí/No)
- Puedo comparar resultados de diferentes ejecuciones accediendo al historial (US-026)

**Historias de Usuario Relacionadas:** US-021, US-022, US-026, US-030

**Estimación:** 5 puntos  
**Prioridad:** Media

---

### US-026: Ver historial de filtrados ejecutados
**Como** Reclutador  
**Quiero** consultar filtrados anteriores de una oferta  
**Para** comparar resultados con diferentes criterios y analizar evolución

**Criterios de Aceptación:**
- Veo lista de filtrados ejecutados ordenados cronológicamente (más reciente primero)
- Cada entrada muestra:
  - Fecha y hora de ejecución completa
  - Usuario que ejecutó el filtrado
  - Resumen de criterios usados (palabras clave, habilidades principales, ponderaciones)
- Veo estadísticas resumidas de cada filtrado:
  - Número de candidatos procesados
  - Número de candidatos exitosos (scoring ≥ 60)
  - Número de candidatos fallidos (scoring < 40)
  - Scoring promedio del filtrado
  - Duración del proceso en segundos
  - Distribución por categoría: X Excelentes, Y Buenos, Z Regulares, W Bajos
- Puedo hacer clic en cualquier filtrado histórico para ver sus resultados detallados (los scores se conservan)
- Puedo identificar visualmente cuál es el filtrado actualmente activo (badge "Activo")
- Los filtrados se mantienen por 6 meses para análisis histórico

**Historias de Usuario Relacionadas:** US-022, US-025, US-030

**Estimación:** 5 puntos  
**Prioridad:** Baja

---

## Épica 5: Autenticación y Seguridad

### US-030: Iniciar sesión en el sistema
**Como** Reclutador  
**Quiero** acceder al sistema con mis credenciales  
**Para** usar las funcionalidades de forma segura

**Criterios de Aceptación:**
- Puedo ingresar email y contraseña en formulario de login
- El sistema valida formato de email antes de enviar
- El sistema valida que ambos campos estén llenos
- Si las credenciales son correctas, accedo al dashboard principal
- Si las credenciales son incorrectas, veo mensaje de error: "Email o contraseña incorrectos"
- Después de 5 intentos fallidos consecutivos, mi cuenta se bloquea temporalmente por 15 minutos
- Veo mensaje claro cuando mi cuenta está bloqueada: "Cuenta bloqueada por múltiples intentos fallidos. Intenta nuevamente en X minutos"
- Mi sesión expira automáticamente después de 8 horas de inactividad
- Al expirar la sesión, soy redirigido al login con mensaje: "Tu sesión ha expirado. Por favor, inicia sesión nuevamente"
- El sistema valida que el email sea único (no puede haber dos usuarios con mismo email)

**Historias de Usuario Relacionadas:** Ninguna (es prerequisito de todas las demás)

**Estimación:** 5 puntos  
**Prioridad:** Alta

---

### US-031: Cerrar sesión en el sistema
**Como** Reclutador  
**Quiero** salir del sistema de forma segura  
**Para** proteger mi cuenta cuando termine de trabajar

**Criterios de Aceptación:**
- Puedo cerrar sesión desde cualquier pantalla mediante botón/menú visible en header
- El botón de cerrar sesión está siempre accesible (icono o texto "Cerrar sesión")
- El sistema invalida mi token JWT inmediatamente al cerrar sesión
- Soy redirigido a la pantalla de login
- No puedo usar el botón "Atrás" del navegador para acceder nuevamente sin autenticar
- Veo mensaje de confirmación: "Sesión cerrada exitosamente"
- El sistema registra en auditoría: fecha/hora del logout y usuario

**Historias de Usuario Relacionadas:** US-030

**Estimación:** 2 puntos  
**Prioridad:** Alta

---

### US-032: Ver perfil de mi usuario
**Como** Reclutador  
**Quiero** consultar la información de mi cuenta  
**Para** verificar mis datos y configuración

**Criterios de Aceptación:**
- Veo mi nombre completo
- Veo mi email registrado (no editable)
- Veo mi rol: Admin o Reclutador
- Veo fecha de mi última sesión (día/mes/año hora:minuto)
- Veo fecha de creación de mi cuenta
- Veo estado de mi cuenta: Activa o Bloqueada
- Puedo acceder a esta vista desde menú de usuario (clic en icono/nombre en header)
- La vista es de solo lectura (no puedo editar datos en el MVP)

**Historias de Usuario Relacionadas:** US-030

**Estimación:** 3 puntos  
**Prioridad:** Baja

---

## Épica 6: Configuración del Sistema

### US-033: Configurar credenciales de portales externos
**Como** Administrador  
**Quiero** configurar las credenciales de APIs de portales  
**Para** habilitar la publicación automática de ofertas

**Criterios de Aceptación:**
- Solo usuarios con rol Admin pueden acceder a esta funcionalidad
- Puedo ingresar credenciales específicas por cada portal:
  - **LinkedIn:** Client ID, Client Secret
  - **Indeed:** API Key
  - **CompuTrabajo:** API Key, API Secret
- Puedo activar/desactivar cada portal (toggle on/off)
- Puedo probar la conexión con cada portal mediante botón "Probar Conexión"
- Al probar conexión, veo resultado inmediato:
  - ✓ Conexión Exitosa (verde): muestra "Autenticación correcta con [portal]"
  - ✗ Error (rojo): muestra mensaje específico del error (credenciales inválidas, sin internet, API no disponible)
- Las credenciales quedan almacenadas de forma encriptada en la base de datos (AES-256)
- Puedo editar credenciales existentes (se requiere confirmación)
- Al guardar, veo confirmación: "Credenciales guardadas y encriptadas exitosamente"
- Veo fecha de última actualización de credenciales por portal
- Veo fecha de última sincronización exitosa con cada portal

**Historias de Usuario Relacionadas:** US-030, US-013

**Estimación:** 8 puntos  
**Prioridad:** Alta

---

### US-034: Gestionar catálogo de habilidades
**Como** Administrador  
**Quiero** mantener un catálogo de habilidades disponibles  
**Para** estandarizar la información en el sistema y facilitar búsquedas

**Criterios de Aceptación:**
- Solo usuarios con rol Admin pueden gestionar el catálogo
- **Agregar habilidad:**
  - Puedo agregar nuevas habilidades con nombre único (no duplicados)
  - Puedo categorizar cada habilidad como: Técnica o Blanda
  - Puedo agregar descripción opcional (texto corto, ej: "Lenguaje de programación para desarrollo web")
  - Al guardar, veo confirmación: "Habilidad agregada exitosamente"
- **Editar habilidad:**
  - Puedo editar nombre, categoría y descripción de habilidades existentes
  - El sistema valida que el nuevo nombre no esté duplicado
- **Desactivar habilidad:**
  - Puedo desactivar habilidades obsoletas (no se eliminan físicamente)
  - Al desactivar, el sistema me advierte: "Esta habilidad está asociada a X candidatos. ¿Deseas desactivarla?"
  - Las habilidades desactivadas NO se eliminan de perfiles de candidatos existentes
  - Las habilidades desactivadas NO aparecen en selectores de US-004 y US-021 (solo activas)
  - Las habilidades desactivadas se muestran en listado con badge "Inactiva" (filtro separado)
- Puedo buscar habilidades por nombre (búsqueda parcial)
- Puedo filtrar por categoría (Técnicas / Blandas / Todas)
- Puedo filtrar por estado (Activas / Inactivas / Todas)
- Veo contador de candidatos que tienen cada habilidad
- El catálogo viene precargado con al menos 50 habilidades comunes (ej: Python, JavaScript, Excel, Liderazgo, Trabajo en Equipo)

**Historias de Usuario Relacionadas:** US-030, US-004, US-021

**Estimación:** 5 puntos  
**Prioridad:** Media

---

## Resumen de Historias de Usuario

**Total de Historias:** 28
**Puntos de Historia Estimados:** 158 puntos

### Distribución por Épica:
- **Gestión de Candidatos:** 11 historias (60 puntos)
- **Publicación de Ofertas:** 6 historias (39 puntos)
- **Gestión de Aplicaciones:** 3 historias (13 puntos)
- **Filtrado Inteligente con IA:** 6 historias (38 puntos)
- **Autenticación y Seguridad:** 3 historias (10 puntos)
- **Configuración del Sistema:** 2 historias (13 puntos)

### Distribución por Prioridad:
- **Alta:** 18 historias (108 puntos)
- **Media:** 7 historias (37 puntos)
- **Baja:** 3 historias (13 puntos)

---

## Criterios de Aceptación Generales

Todas las historias de usuario deben cumplir con:
- ✅ Interfaz responsive y usable (mínimo 1280px de ancho)
- ✅ Validaciones de campos obligatorios con mensajes claros
- ✅ Mensajes de error específicos y comprensibles (sin códigos técnicos)
- ✅ Confirmaciones visuales de acciones exitosas (notificaciones toast o modales)
- ✅ Tiempos de respuesta según RNF especificados en el PRD
- ✅ Cumplimiento de estándares de seguridad (encriptación, validaciones)
- ✅ Accesibilidad básica (contraste WCAG 2.1 AA, labels en formularios)
- ✅ Auditoría de operaciones críticas (crear, actualizar, eliminar)

---

## Notas para el Equipo de Desarrollo

### Estimaciones
- Basadas en puntos de historia usando escala Fibonacci (1, 2, 3, 5, 8, 13)
- Velocidad esperada: 20-25 puntos por sprint (equipo de 3 desarrolladores)
- Duración estimada: 7-8 sprints para completar MVP (reducción de 2 sprints vs v2.0)

### Testing Crítico

**Performance:**
- US-022: Filtrado para 100 candidatos < 30 segundos
- US-006/007: Búsquedas con 10,000 perfiles < 2 segundos
- US-013: Publicación simultánea en 3 portales < 5 minutos

**Integración:**
- US-013: Publicación real en portales externos (sandbox primero)
- US-022: Análisis NLP con documentos reales
- US-030: Bloqueo de cuenta después de 5 intentos

**Seguridad:**
- US-033: Credenciales encriptadas AES-256
- US-005: Documentos almacenados encriptados
- US-011: Auditoría completa de operaciones GDPR

### Definition of Done (DoD)

Cada US se considera completa cuando:
- ✅ Código desarrollado y code review aprobado por al menos 1 peer
- ✅ Pruebas unitarias escritas y pasando (cobertura >70% del código nuevo)
- ✅ Pruebas de integración pasando (para US con dependencias externas)
- ✅ Todos los criterios de aceptación validados por PO (sesión de demo)
- ✅ Documentación técnica actualizada (Swagger para endpoints nuevos)
- ✅ Deploy en ambiente de staging exitoso
- ✅ Sin bugs críticos (P0) o blockers pendientes
- ✅ Performance según SLA validado (cuando aplique)

---

## Glosario de Términos

- **Scoring**: Puntuación de compatibilidad entre candidato y oferta (0-100)
- **Portal Externo**: Plataforma de empleo externa (LinkedIn, Indeed, CompuTrabajo)
- **Multiposting**: Publicación simultánea en múltiples portales con un solo clic
- **NLP**: Natural Language Processing - Análisis de texto mediante IA
- **Motor de IA**: Componente de Workers Python que ejecuta análisis semántico
- **Worker**: Proceso asíncrono separado que ejecuta tareas pesadas
- **Eliminación Lógica**: Marcar registro como eliminado sin borrarlo físicamente (campo deleted=true)
- **JWT**: JSON Web Token - Token de autenticación con expiración
- **API Key**: Clave de autenticación para APIs externas
- **CRUD**: Create, Read, Update, Delete - Operaciones básicas de datos
- **Criterio de Filtrado**: Conjunto de parámetros para evaluar candidatos con IA
- **Plantilla**: Criterio de filtrado guardado para reutilizar en otras ofertas
- **Disponibilidad**: Estado que indica si candidato puede comenzar inmediatamente o desde fecha futura
- **Visibilidad**: Configuración de oferta (Pública: todos pueden aplicar / Privada: solo invitados)

---

## Matriz de Dependencias

| Historia | Depende de | Es prerequisito de |
|----------|------------|-------------------|
| US-001 | US-030 | US-002, US-003, US-004, US-005, US-006, US-007, US-008, US-009, US-010, US-011 |
| US-004 | US-001, US-034 | US-007, US-021 |
| US-009 | US-001 | US-011 |
| US-010 | US-001, US-018 | US-011 |
| US-012 | US-030 | US-013, US-016, US-017, US-018, US-021 |
| US-013 | US-012, US-033 | US-014, US-015 |
| US-018 | US-012, US-013 | US-019, US-020, US-021, US-022 |
| US-021 | US-012, US-018, US-034 | US-022 |
| US-022 | US-021, US-018 | US-023, US-024, US-025, US-026 |
| US-030 | Ninguna | Todas las demás |
| US-033 | US-030 | US-013 |
| US-034 | US-030 | US-004, US-021 |

---

## Elementos Fuera de Scope del MVP

Los siguientes elementos están en el modelo de datos o fueron mencionados en documentos, pero **NO se implementan en el MVP**:

### Tabla FEEDBACK_IA
- **Razón**: Sistema de feedback loop para mejorar IA requiere ML avanzado
- **Futuro**: v2.0 - Implementar aprendizaje continuo

### Métricas de Engagement de Portales
- **Campos**: visualizaciones, clics en PUBLICACION_PORTAL
- **Razón**: APIs de portales no siempre proveen estas métricas en tiempo real
- **Futuro**: v2.0 - Dashboard analítico de ofertas

### Sistema de Créditos
- **Campo**: creditos_consumidos en RESULTADO_FILTRADO
- **Razón**: MVP es on-premise sin billing
- **Futuro**: v3.0 - Modelo SaaS con pricing por uso de IA

### Edición de Ofertas Publicadas
- **Razón**: Complejidad de sincronizar cambios en portales externos
- **Futuro**: v2.0 - Sincronización bidireccional

### Notificaciones Push/Email
- **Razón**: Requiere infraestructura adicional (SMTP, WebSockets)
- **Futuro**: v2.0 - Sistema de notificaciones completo

---

**Documento generado:** Octubre 2025  
**Versión:** 3.0  
**Para:** Equipo Scrum LTI MVP  
**Aprobado por:** Javier Siancas

***

## 2. Product Backlog

# Product Backlog Priorizado (MVP LTI - Versión 3.0)

Este Product Backlog ha sido priorizado (de mayor a menor prioridad) utilizando una matriz de análisis basada en los criterios: Valor de Negocio, Dependencias, Riesgos y Madurez Tecnológica. Este orden define la secuencia de implementación recomendada para el MVP.

## Épica 5: Autenticación y Seguridad (Habilitador Principal)

1.  Iniciar sesión en el sistema (US-030)
2.  Cerrar sesión en el sistema (US-031)

## Épica 1: Gestión de Candidatos (Módulo Base)

3.  Crear perfil básico de candidato (US-001)
4.  Gestionar catálogo de habilidades (US-034)
5.  Agregar habilidades e idiomas a candidato (US-004)
6.  Agregar experiencia laboral a candidato (US-002)
7.  Agregar formación académica y certificaciones a candidato (US-003)
8.  Adjuntar documentos a perfil de candidato (US-005)
9.  Buscar candidatos por criterios básicos (US-006)
10. Ver detalle completo de candidato (US-008)
11. Actualizar información de candidato (US-009)
12. Eliminar perfil de candidato (US-010)
13. Buscar candidatos por habilidades e idiomas (US-007)

## Épica 2: Publicación de Ofertas Laborales (Habilitador Secundario)

14. Crear oferta laboral completa (US-012)
15. Configurar credenciales de portales externos (US-033)
16. Publicar oferta en múltiples portales (US-013)
17. Consultar ofertas activas (US-016)
18. Ver estado de publicación por portal (US-014)
19. Ver detalle completo de oferta (US-017)
20. Ver logs de errores de publicación (US-015)

## Épica 4: Filtrado Inteligente con IA (Valor Diferenciador)

21. Definir criterios de filtrado para oferta (US-021)
22. Ver candidatos aplicados a oferta (US-018)
23. Ejecutar filtrado automático con IA (US-022)
24. Ver resultados de filtrado con scoring (US-023)
25. Ver justificación detallada de scoring (US-024)
26. Ajustar criterios y re-ejecutar filtrado (US-025)

## Épica 3: Gestión de Aplicaciones (Flujo de Trabajo)

27. Cambiar estado de aplicación (US-019)
28. Agregar notas a aplicación (US-020)

## Historias de Baja Prioridad / Auditoría (Cleanup y Cumplimiento)

29. Ver perfil de mi usuario (US-032)
30. Ver historial de cambios de candidato (US-011)
31. Ver historial de filtrados ejecutados (US-026)

---
**Total de Historias:** 31

***

## 3. Tickets de Trabajo - US-001

# Tickets de Trabajo para US-001: Crear perfil básico de candidato

**Historia de Usuario Padre:** US-001: Crear perfil básico de candidato
**Estimación de la US Padre:** 5 Puntos de Historia (PH)
**Módulo Principal:** Gestión de Candidatos (CU-01)
**Stack Tecnológico:** React, Node.js, Express, Prisma ORM

---

## Ticket 1/5: UI - Formulario de Creación de Perfil Básico

| Campo | Detalle |
| :--- | :--- |
| **Estimación (PH)** | **2** |
| **Tipo de ticket** | Característica |
| **Módulo del producto** | UI / Frontend (React Web Application) |
| **Título** | Desarrollar Formulario de Creación de Perfil Básico |
| **Prioridad del ticket** | **Alta** |
| **Responsable (Propuesto)** | Developer A (Frontend) |
| **Historial de cambios** | 2025-10-27: Creación del ticket |
| **Documentos relacionados** | US-001, CU-01 (Subflujo 1) |

**Justificación de Estimación (2 PH):**
Baja complejidad. Es un componente de formulario estático con campos básicos y una validación de formato simple en el lado del cliente (React). El riesgo es mínimo.

---

## Ticket 2/5: BE - Endpoint POST /candidatos y Modelo de Datos

| Campo | Detalle |
| :--- | :--- |
| **Estimación (PH)** | **3** |
| **Tipo de ticket** | Característica |
| **Módulo del producto** | Backend (Servidor de Aplicación - Node.js) |
| **Título** | BE: Implementar Endpoint POST para Crear Candidato |
| **Prioridad del ticket** | **Alta** |
| **Responsable (Propuesto)** | Developer B (Backend) |
| **Historial de cambios** | 2025-10-27: Creación del ticket |
| **Documentos relacionados** | US-001, Arquitectura de Alto Nivel, US-030 |

**Justificación de Estimación (3 PH):**
Complejidad media. Implica la creación del modelo de datos inicial en **Prisma ORM**, la definición de la ruta `POST` en Express.js y la lógica de persistencia. Es más complejo que el formulario UI, pero no incluye las validaciones ni la auditoría.

---

## Ticket 3/5: BE - Implementación de Validaciones de Unicidad y Formato

| Campo | Detalle |
| :--- | :--- |
| **Estimación (PH)** | **5** |
| **Tipo de ticket** | Tarea Técnica / Característica |
| **Módulo del producto** | Backend / Core Logic |
| **Título** | BE: Validaciones de Unicidad (Email) y Formato (URL/Teléfono) |
| **Prioridad del ticket** | **Alta** |
| **Responsable (Propuesto)** | Developer B (Backend) |
| **Historial de cambios** | 2025-10-27: Creación del ticket |
| **Documentos relacionados** | US-001, CU-01 (RN-01, FA-01) |

**Justificación de Estimación (5 PH):**
Alta complejidad. Este es el ticket más grande del *backend* para esta US. Requiere lógica de negocio crítica:
1.  Consulta a la BD para validar **unicidad de email** (alto riesgo de fallo si no se maneja transaccionalmente).
2.  Implementación de **múltiples validaciones de formato** (email, teléfono, URL) que requieren pruebas unitarias exhaustivas para cumplir el **DoD (>70% de cobertura)**.

---

## Ticket 4/5: Tech Task - Auditoría de Creación de Perfil

| Campo | Detalle |
| :--- | :--- |
| **Estimación (PH)** | **3** |
| **Tipo de ticket** | Tarea Técnica |
| **Módulo del producto** | Backend / Seguridad (Autenticación y Auditoría) |
| **Título** | BE: Registro de Auditoría para la Creación de Candidato (US-001) |
| **Prioridad del ticket** | **Alta** |
| **Responsable (Propuesto)** | Developer B (Backend/Seguridad) |
| **Historial de cambios** | 2025-10-27: Creación del ticket |
| **Documentos relacionados** | US-001 (DoD - Auditoría), Arquitectura de Alto Nivel, CU-01 (RN-04) |

**Justificación de Estimación (3 PH):**
Complejidad media. Requiere configurar el patrón de auditoría (ej. *middleware* o *hooks* de Prisma) para obtener el `ID_Usuario` del JWT y registrar el evento. Es un esfuerzo considerable la **primera vez** que se implementa, pero luego se reutilizará.

---

## Ticket 5/5: INT - Integración del Flujo y Manejo de Mensajes

| Campo | Detalle |
| :--- | :--- |
| **Estimación (PH)** | **3** |
| **Tipo de ticket** | Tarea Técnica / Integración |
| **Módulo del producto** | UI / Integración Frontend-Backend |
| **Título** | INT: Conectar Formulario con BE y Manejar Confirmaciones/Errores |
| **Prioridad del ticket** | **Alta** |
| **Responsable (Propuesto)** | Developer A (Frontend) |
| **Historial de cambios** | 2025-10-27: Creación del ticket |
| **Documentos relacionados** | US-001 (CA), CU-01 |

**Justificación de Estimación (3 PH):**
Complejidad media. El riesgo aquí no es la conexión en sí, sino asegurar que el *frontend* maneje correctamente **todos los posibles errores** del *backend* (409 de Unicidad, 400 de Formato, 500 de Servidor) y mapee los mensajes de error a los campos correctos para una buena UX, además de manejar la navegación/redirección final.

---

### Resumen de la Estimación

| Ticket | Módulo | Estimación (PH) |
| :--- | :--- | :---: |
| Ticket 1/5 | UI | 2 |
| Ticket 2/5 | BE | 3 |
| Ticket 3/5 | BE | 5 |
| Ticket 4/5 | Tech Task | 3 |
| Ticket 5/5 | INT | 3 |
| **TOTAL US-001** | | **16** |

**Nota:** La suma de los *Story Points* de los tickets (**16 PH**) es mayor que la estimación inicial de la Historia de Usuario (**5 PH**). Esto es común y correcto en SCRUM, ya que el desglose detalla la complejidad real. La estimación de **5 PH** original fue solo una aproximación a alto nivel. La nueva estimación de **16 PH** es más precisa para la planificación del Sprint.
