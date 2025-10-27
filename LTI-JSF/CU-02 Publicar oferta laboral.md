# CU-02: Publicar Oferta Laboral

## Identificador
**CU-02**

## Nombre
Publicar Oferta Laboral

## Actores
- **Principal:** Reclutador
- **Secundarios:** Sistema de Portal Externo, Base de Datos de Ofertas

## Descripción
Este caso de uso permite al Reclutador crear una oferta de trabajo completa y publicarla simultáneamente en múltiples portales de empleo externos. El Reclutador define todos los detalles de la vacante incluyendo título del puesto, descripción detallada de responsabilidades, requisitos técnicos y competencias blandas necesarias, beneficios ofrecidos, rango salarial, ubicación física o remota, y modalidad de trabajo. Una vez creada la oferta, el Reclutador selecciona los portales de empleo donde desea publicarla (LinkedIn, Indeed, CompuTrabajo, Bumeran, etc.). El sistema almacena la oferta en la base de datos y distribuye automáticamente el contenido a las plataformas seleccionadas mediante sus APIs correspondientes, adaptando el formato según los requerimientos de cada portal.

## Precondiciones
- El Reclutador debe estar autenticado en el sistema
- El Reclutador debe tener permisos para publicar ofertas
- Los portales externos deben estar configurados y con credenciales válidas

## Postcondiciones
### Éxito
La oferta queda almacenada en la base de datos y publicada en los portales seleccionados

### Fallo
Se muestra mensaje de error indicando qué portales fallaron en la publicación

## Flujo Principal (Escenario Exitoso)

### Crear y Publicar Oferta
1. El Reclutador selecciona la opción "Crear Nueva Oferta"
2. El sistema presenta el formulario de creación de oferta
3. El Reclutador ingresa título del puesto y descripción detallada
4. El Reclutador especifica requisitos técnicos y experiencia requerida
5. El Reclutador define beneficios y rango salarial
6. El Reclutador establece ubicación y modalidad de trabajo
7. El Reclutador selecciona los portales donde publicar la oferta
8. El sistema almacena la oferta en la base de datos
9. El sistema distribuye la oferta a cada portal externo seleccionado
10. Los sistemas de portales externos confirman la recepción
11. El sistema confirma la publicación exitosa en todos los portales

### Consultar Estado de Publicación
1. El Reclutador accede al módulo de ofertas activas
2. El Reclutador selecciona una oferta publicada
3. El sistema consulta la base de datos
4. El sistema muestra el detalle de la oferta y estado en cada portal
5. El sistema indica portales donde está activa, pausada o con errores

## Requerimientos Especiales
- El sistema debe soportar al menos 5 portales externos simultáneamente
- La distribución a portales debe completarse en menos de 5 minutos
- El sistema debe guardar logs de errores de publicación para troubleshooting
- El formato de la oferta debe adaptarse automáticamente a cada portal

## Frecuencia de Uso
**Media-Alta** - Varias veces por semana