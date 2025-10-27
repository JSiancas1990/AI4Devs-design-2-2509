Herramienta: Claude Sonne 4.5

## Prompt 1:
Eres un experto analista de requerimientos de software. Explícame brevemente qué es un PRD (Product Requirements Document) y cuál debe ser su estructura.

## Prompt 2:
Según lo que me has explicado sobre el PRD, elabora uno en formato Markdown (.md) listo para descargar para el MVP del sistema ATS llamado "LTI". Toma en consideración todo lo necesario que encuentres en los documentos que estoy adjuntando y no inventes nada. El propósito de este documento es elaborar posteriormente las historias de usuario.

Nota: Los documento que adjunté fueron la descripción y funcionalidades del sistema, tres casos de uso del MVP, el modelo de datos y el diagrama de arquitectura de alto nivel.

## Prompt 3:
Como un experto analista de requerimientos y especialista en la metodología ágil SCRUM, requiero que generes las historias de usuario (US) del MVP de acuerdo PRD del sistema LTI que has generado. 

Considera lo siguiente por cada US: 
* Debe seguir la plantilla clásica: "Como  [usuario], quiero [funcionalidad] para [beneficio]". 
* Debe ser lo suficientemente breve como para escribirla en un post-it.
* Debe ser lo suficientemente breve como se complete en máximo 1 sprint (2 semanas).
* Debes evitar los detalles técnicos o instrucciones de implementación.

Como resultado, entrégame todas las US en un archivo en formato Markdown (.md) listo para descargar.

## Prompt 4:
De acuerdo al documento que has generado, requiero que me expliques lo siguiente:
* ¿Qué valor de negocio aporta el US-011?
* ¿A qué se refiere el criterio de aceptación "Puedo filtrar por tipo de operación" del US-011 y cuáles son los tipos de operación a los que se refiere? Si ya están definidos, indícame en qué archivo.

## Prompt 5:
Vuelve a generar el archivo tomando en cuenta estas acciones:
* Agregar aclaraciones si los criterios de aceptación no son claros, sobre todo, con aquellos que implican tipos de algo que no están listados. Por ejemplo, el criterio de aceptación "Puedo filtrar por tipo de operación" del US-011 debería listar cuáles son los tipos de operación.
* Especificar por cada US qué relación o dependencia tiene de otras US. Por ejemplo, entiendo que el US-030 es requisito para todas las funcionalidades del sistema. Agregar un punto titulado "Historias de Usuario Relacionadas" y listar ahí solo el identificador de las US. Por ejemplo:  "Historias de Usuario Relacionadas: US-030, US-031 y US-032". Si es posible, que cada uno de los identificadores sea un hipervínculo.

## Prompt 6:
De acuerdo a la última versión del documento que has generado, requiero que me expliques breve y puntualmente lo siguiente:
* ¿Por qué has agregado nuevas historias de usuario? Por ejemplo, la US-029 y demás.
* Según la US-006, los candidatos tienen disponibilidad. ¿En qué momento se agrega la disponibilidad de un candidato? ¿Se registran en el US-001 con algún valor por defecto para ese campo?
* Según la US-008, los candidatos tienen enlaces profesionales. ¿En qué momento se llenan estos campos? No veo que estén definidos en otro lado.

## Prompt 7:
Para estar seguros, requiero que revises todo el documento, identifiques todas las inconsistencias y las listes.

## Prompt 8:
Requiero que resuelvas todas las inconsistencias en el documento de historias de usuario y vuelvas a generar un archivo en formato Markdown listo para descargar. En la medida de lo posible, no agregues nuevas historias de usuario, sino modifica o eliminar las que sugieres. Si consideras necesario modificar el PRD, indícame qué cambios serían.

## Prompt 9:
Sí, genera nuevamente el PRD con los cambios sugeridos.

Herramienta: Gemini

## Prompt 10:
Eres un experto en análisis de requerimientos de software utilizando el framework SCRUM. Usando el documento adjunto de historias de usuario, requiero que generes un Product Backlog para el MVP utilizando una metodología basada en importancia o necesidad. Como resultado, espero lo siguiente en un solo archivo:
* Matriz que contenga el valor "alto", "medio" o "bajo" para cada historia de usuario en los siguientes criterios: valor de negocio (incluye a los usuarios finales), dependencias, riegos y madurez tecnológica.
* El Product Backlog con las historias de usuario priorizadas (de mayor prioridad a menor) como resultado del análisis hecho en la matriz, de modo que esa priorización genere un orden de implementación único. Este orden definirá qué harán los equipos en las próximas iteraciones. Considera solamente listar los títulos sin mayores detalles.
El archivo deberá estar en formato Markdown.

Nota: Este es el prompt que me generó un resultado más lógico porque consideró las historias de usuario de configuración previas a las historias de usuario dependientes. En otros intentos, las historias de usuario de configuración tenían menor prioridad según el valor de negocio, pero el asistente dejaba la nota de que se podían encontrar soluciones alternativas a las historias de usuario dependientes para que puedan ser implementadas (llaves de configuración en duro, etc.) 

## Prompt 11:
Según los documentos que adjunto (historias de usuario, arquitectura y caso de uso relacionado), requiero que generes los tickets de trabajo necesarios de la US-001. 
Por cada ticket de trabajo, espero lo siguiente:
* Tipo de ticket (característica, tarea técnica, error, spike)
* Módulo del producto: (UI, backend, etc.)
* Título y descripción detallada
* Criterios de aceptación detallados
* Prioridad del ticket
* Responsable
* Historial de cambios
* Documentos relacionados (estos son los documentos en donde se podría encontrar mayor detalle o contexto para la ejecución de la tarea; por ejemplo, el PRD, los casos de uso, etc.)
Considera que los tickets de trabajo cumplan con todos los criterios de aceptación y el DoD (Definition of Done). Además, detalla los ajustes tecnológicos necesarios.
El archivo deberá estar en formato Markdown listo para descargar.

## Prompt 12:
Según el documento que has creado, ¿no hay conflicto entre el ticket 4 y la US-011? Todo lo relacionado a la auditoría está pensando en implementarse al final.

Respuesta del asistente: El Ticket 4 de la US-001 es una Tarea Técnica de Infraestructura y Seguridad que sienta las bases de auditoría requeridas por el DoD. La US-011 es una Característica de la Interfaz de Usuario que consume los resultados de esa auditoría y, por lo tanto, puede ser pospuesta. No hay conflicto; el Ticket 4 es un habilitador (enabling feature) de la US-011.

## Prompt 13:
Finalmente, requiero estimar los tickets de trabajo usando la metodología fibonacci. Añade la estimación al archivo en formato Markdown listo para descargar.
