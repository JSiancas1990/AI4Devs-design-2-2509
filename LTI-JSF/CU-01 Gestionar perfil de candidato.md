# CU-01: Gestionar Perfil de Candidato

## Información General

### Identificador
**CU-01**

### Nombre
Gestionar Perfil de Candidato

### Versión
1.0

### Prioridad
Alta - Funcionalidad crítica para el MVP

---

## Actores

### Actores Principales
- **Reclutador**: Profesional de recursos humanos responsable de gestionar candidatos y vacantes

### Actores Secundarios
- **Base de Datos de Candidatos**: Sistema de almacenamiento que persiste la información de perfiles

---

## Descripción

Este caso de uso permite al Reclutador gestionar de manera centralizada todos los perfiles de candidatos dentro del sistema LTI. El Reclutador puede crear nuevos perfiles ingresando información completa del candidato (datos personales, experiencia laboral, educación, habilidades técnicas y blandas, idiomas, certificaciones), consultar perfiles existentes mediante búsquedas avanzadas con múltiples filtros, actualizar información cuando el candidato proporcione datos nuevos o corregidos, y eliminar perfiles duplicados u obsoletos. 

El sistema valida automáticamente los datos ingresados para garantizar integridad y consistencia, almacena documentos adjuntos como currículums vitae, cartas de presentación y certificados, y mantiene un historial de cambios para auditoría. Esta funcionalidad es la base fundamental del ATS, ya que centraliza toda la información de candidatos en una ubicación accesible y organizada.

---

## Precondiciones

1. El Reclutador debe estar autenticado en el sistema LTI
2. El Reclutador debe tener permisos y rol activo de "Reclutador" o superior
3. La Base de Datos de Candidatos debe estar disponible y operativa
4. Para actualizar o eliminar: el perfil del candidato debe existir previamente en el sistema

---

## Postcondiciones

### Escenario Exitoso
- El perfil del candidato queda correctamente almacenado/actualizado/eliminado en la Base de Datos
- El sistema registra la operación en el log de auditoría con timestamp y usuario responsable
- La información está disponible inmediatamente para consultas y otros procesos
- Se envía confirmación visual al Reclutador sobre la operación exitosa

### Escenario Fallido
- No se realizan cambios en la Base de Datos
- Se muestra mensaje de error específico al Reclutador indicando la causa del fallo
- El sistema registra el error en el log para análisis técnico
- Los datos temporales ingresados se conservan en sesión para evitar pérdida de información

---

## Flujo Principal (Escenario Exitoso)

### Subflujo 1: Crear Perfil de Candidato

1. El Reclutador accede al módulo "Gestión de Candidatos"
2. El Reclutador selecciona la opción "Crear Nuevo Candidato"
3. El sistema presenta el formulario de registro con campos obligatorios y opcionales
4. El Reclutador ingresa datos personales del candidato:
   - Nombre completo
   - Correo electrónico
   - Teléfono de contacto
   - Ubicación geográfica (ciudad, país)
   - Enlace a perfil profesional (LinkedIn, portafolio)
5. El Reclutador ingresa experiencia laboral:
   - Empresas anteriores
   - Cargos desempeñados
   - Duración en cada posición
   - Responsabilidades principales
6. El Reclutador ingresa formación académica:
   - Instituciones educativas
   - Títulos obtenidos
   - Áreas de estudio
   - Años de graduación
7. El Reclutador ingresa habilidades y competencias:
   - Habilidades técnicas (hard skills)
   - Competencias blandas (soft skills)
   - Nivel de dominio de cada habilidad
8. El Reclutador adjunta documentos relevantes:
   - Currículum vitae (PDF, DOC, DOCX)
   - Carta de presentación
   - Certificados y diplomas
9. El sistema valida automáticamente:
   - Formato de correo electrónico
   - Formato de teléfono
   - Tamaño y tipo de archivos adjuntos
   - Campos obligatorios completos
10. El Reclutador revisa la información ingresada
11. El Reclutador confirma la creación del perfil
12. El sistema almacena el perfil en la Base de Datos de Candidatos
13. El sistema genera un ID único para el candidato
14. El sistema muestra confirmación de creación exitosa con el ID asignado

### Subflujo 2: Consultar Perfil de Candidato

1. El Reclutador accede al módulo "Gestión de Candidatos"
2. El Reclutador ingresa criterios de búsqueda:
   - Por nombre del candidato
   - Por habilidades específicas
   - Por años de experiencia
   - Por ubicación geográfica
   - Por disponibilidad
   - Combinación de múltiples criterios
3. El sistema consulta la Base de Datos de Candidatos
4. El sistema aplica los filtros especificados
5. El sistema presenta una lista de candidatos que coinciden con los criterios
6. El sistema muestra vista previa con información relevante de cada candidato
7. El Reclutador selecciona un candidato de la lista
8. El sistema recupera el perfil completo de la Base de Datos
9. El sistema presenta todos los detalles del candidato en pantalla
10. El sistema muestra documentos adjuntos disponibles para descarga

### Subflujo 3: Actualizar Perfil de Candidato

1. El Reclutador consulta y selecciona un candidato existente (según Subflujo 2)
2. El Reclutador selecciona la opción "Editar Perfil"
3. El sistema presenta el formulario prellenado con los datos actuales
4. El sistema habilita los campos para edición
5. El Reclutador modifica la información necesaria:
   - Actualiza datos de contacto
   - Agrega nueva experiencia laboral
   - Actualiza habilidades adquiridas
   - Reemplaza o agrega documentos
6. El sistema valida los cambios realizados
7. El Reclutador revisa las modificaciones
8. El Reclutador confirma la actualización
9. El sistema actualiza el perfil en la Base de Datos de Candidatos
10. El sistema registra el historial de cambios con fecha y usuario
11. El sistema muestra confirmación de actualización exitosa

### Subflujo 4: Eliminar Perfil de Candidato

1. El Reclutador consulta y selecciona un candidato existente (según Subflujo 2)
2. El Reclutador selecciona la opción "Eliminar Perfil"
3. El sistema muestra advertencia sobre la eliminación permanente
4. El sistema solicita confirmación explícita de eliminación
5. El sistema muestra resumen del candidato a eliminar
6. El Reclutador confirma la eliminación
7. El sistema verifica que el perfil no esté vinculado a procesos activos
8. El sistema marca el perfil como eliminado en la Base de Datos (eliminación lógica)
9. El sistema archiva los documentos asociados
10. El sistema registra la eliminación en el log de auditoría
11. El sistema muestra confirmación de eliminación exitosa
12. El sistema redirige al Reclutador al listado de candidatos

---

## Flujos Alternativos

### FA-01: Datos Inválidos al Crear/Actualizar
- **Punto de Divergencia**: Paso 9 de Subflujo 1 o Paso 6 de Subflujo 3
- **Condición**: El sistema detecta errores de validación
- **Acción**: 
  1. El sistema marca los campos con errores en color rojo
  2. El sistema muestra mensajes específicos de error bajo cada campo
  3. El sistema mantiene los datos válidos ingresados
  4. El flujo retorna al paso 4 para corrección

### FA-02: No se Encuentran Candidatos
- **Punto de Divergencia**: Paso 5 de Subflujo 2
- **Condición**: La búsqueda no retorna resultados
- **Acción**:
  1. El sistema muestra mensaje "No se encontraron candidatos con los criterios especificados"
  2. El sistema sugiere ampliar los criterios de búsqueda
  3. El flujo retorna al paso 2 para nueva búsqueda

### FA-03: Cancelación de Eliminación
- **Punto de Divergencia**: Paso 6 de Subflujo 4
- **Condición**: El Reclutador decide no eliminar el perfil
- **Acción**:
  1. El sistema cancela la operación de eliminación
  2. El sistema mantiene el perfil sin cambios
  3. El flujo retorna a la vista de detalle del candidato

---

## Requerimientos Especiales

### Requerimientos de Rendimiento
- El tiempo de respuesta para búsquedas debe ser inferior a 2 segundos para hasta 10,000 perfiles
- El tiempo de carga del perfil completo debe ser inferior a 1 segundo
- El sistema debe soportar hasta 50 usuarios concurrentes creando/editando perfiles

### Requerimientos de Seguridad
- Todos los datos personales deben cumplir con GDPR (Reglamento General de Protección de Datos)
- Todos los datos personales deben cumplir con LOPD (Ley Orgánica de Protección de Datos)
- Los documentos adjuntos deben almacenarse encriptados
- El acceso a perfiles debe estar registrado en logs de auditoría
- Implementar control de acceso basado en roles (RBAC)

### Requerimientos de Usabilidad
- La interfaz debe ser intuitiva y no requerir capacitación formal
- Los campos obligatorios deben estar claramente marcados con asterisco (*)
- Debe existir ayuda contextual (tooltips) en campos complejos
- El formulario debe tener autocompletado para datos comunes (ciudades, habilidades)

### Requerimientos de Almacenamiento
- Los documentos adjuntos no deben exceder 10 MB por archivo
- Formatos permitidos para CV: PDF, DOC, DOCX
- Formatos permitidos para certificados: PDF, JPG, PNG
- El sistema debe mantener historial de cambios por al menos 2 años

### Requerimientos de Disponibilidad
- La Base de Datos debe tener disponibilidad del 99.5%
- Implementar respaldos automáticos diarios
- Tiempo de recuperación ante fallos (RTO): máximo 4 horas

---

## Frecuencia de Uso
**Alta** - Esta funcionalidad se utiliza diariamente múltiples veces por cada Reclutador activo en el sistema. Se estima un promedio de 15-30 operaciones por día por usuario.

---

## Reglas de Negocio

### RN-01: Unicidad de Candidatos
Un candidato se considera único por su correo electrónico. No se permiten duplicados con el mismo email.

### RN-02: Datos Mínimos Requeridos
Para crear un perfil válido se requiere como mínimo: nombre completo, correo electrónico, teléfono y al menos un CV adjunto.

### RN-03: Retención de Datos
Los perfiles eliminados se mantienen en archivo por 90 días antes de eliminación definitiva, cumpliendo con requisitos legales.

### RN-04: Actualización de Perfiles
Cualquier cambio en un perfil debe registrar: fecha, hora, usuario que realizó el cambio y campos modificados.

---

## Supuestos

1. Los Reclutadores tienen conocimientos básicos de informática y navegación web
2. Los candidatos proporcionan información veraz y actualizada
3. La conexión a internet es estable durante las operaciones
4. Los navegadores utilizados soportan JavaScript y son versiones actualizadas

---

## Notas Adicionales

- Este caso de uso es la base fundamental para todos los demás procesos del ATS
- La calidad de los datos ingresados impacta directamente en la efectividad del filtrado automático
- Se recomienda implementar validaciones asíncronas para mejorar la experiencia de usuario
- Considerar integración futura con LinkedIn para importación automática de perfiles