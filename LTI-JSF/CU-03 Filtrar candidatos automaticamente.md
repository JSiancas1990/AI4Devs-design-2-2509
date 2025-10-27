# CU-03: Filtrar Candidatos Automáticamente

## Identificador
**CU-03**

## Nombre
Filtrar Candidatos Automáticamente

## Actores
- **Principal:** Reclutador
- **Secundarios:** Motor de IA, Base de Datos de Candidatos

## Descripción
Este caso de uso permite al Reclutador activar un proceso de filtrado inteligente y automatizado sobre candidatos que han aplicado a una oferta laboral específica. El Reclutador define criterios de filtrado personalizados incluyendo palabras clave obligatorias, habilidades técnicas requeridas, años de experiencia, nivel educativo, y ponderaciones para cada criterio. El sistema utiliza el Motor de IA para analizar automáticamente los currículums de los candidatos aplicados, empleando técnicas de procesamiento de lenguaje natural (NLP) y análisis semántico para identificar coincidencias más allá de keywords exactas. El motor genera un scoring de compatibilidad para cada candidato y presenta una lista priorizada con los mejores matches. El Reclutador puede revisar los resultados, ajustar criterios si es necesario, y validar las recomendaciones antes de avanzar con los candidatos seleccionados.

## Precondiciones
- El Reclutador debe estar autenticado en el sistema
- Debe existir al menos una oferta laboral con candidatos aplicados
- Los perfiles de candidatos deben tener currículums cargados
- Los criterios de filtrado deben estar definidos o usar criterios por defecto

## Postcondiciones
### Éxito
Se genera una lista priorizada de candidatos con scoring de compatibilidad

### Fallo
Se muestra mensaje de error y no se generan recomendaciones

## Flujo Principal (Escenario Exitoso)

### Definir y Ejecutar Filtrado
1. El Reclutador selecciona una oferta laboral activa
2. El Reclutador accede a la opción "Filtrar Candidatos"
3. El sistema muestra los candidatos aplicados a la oferta
4. El Reclutador define criterios de filtrado (palabras clave, habilidades, experiencia mínima)
5. El Reclutador establece ponderaciones para cada criterio
6. El Reclutador inicia el proceso de filtrado
7. El sistema envía los datos al Motor de IA
8. El Motor de IA analiza los currículums contra los criterios definidos
9. El Motor de IA aplica análisis semántico para identificar coincidencias
10. El Motor de IA calcula scoring de compatibilidad para cada candidato
11. El sistema genera ranking de candidatos ordenado por scoring
12. El sistema almacena los resultados en la base de datos
13. El sistema presenta al Reclutador la lista priorizada con detalles de compatibilidad

### Revisar Resultados de Filtrado
1. El Reclutador accede al módulo de ofertas
2. El Reclutador selecciona una oferta con filtrado ejecutado
3. El sistema consulta los resultados en la base de datos
4. El sistema muestra la lista de candidatos recomendados con scoring
5. El Reclutador revisa cada candidato y su justificación de scoring
6. El Reclutador puede aceptar o ajustar las recomendaciones

## Requerimientos Especiales
- El Motor de IA debe soportar análisis de currículums en múltiples formatos (PDF, DOC, DOCX)
- El análisis debe completarse en menos de 30 segundos para hasta 100 candidatos
- El scoring debe presentarse en escala de 0-100 con explicación de factores
- El sistema debe permitir ajustar ponderaciones y re-ejecutar el filtrado
- Debe mantener historial de filtrados anteriores para auditoría

## Frecuencia de Uso
**Alta** - Cada vez que se reciben nuevas aplicaciones a ofertas activas