# Sistema de Información de Gestión de Salud (HMIS) de OpenHIE

Un Sistema de Información de Gestión de Salud (Health Management Information System, HMIS), también llamado Sistema de Información de Salud de Rutina, facilita la recopilación de indicadores periódicos de prestación de servicios de salud y de salud pública a partir de una variedad de sistemas de información y el uso eficaz de la información en instalaciones, distritos y niveles superiores para ayudar a mejorar los resultados de la atención médica.

Consulte también “Requisitos no funcionales”.

## **OpenHIE HMIS Workflow Requirements**&#x20;

The following workflow is currently supported, and an FHIR-based message is emerging.&#x20;

| <p> </p><p>N.º</p>                       | **Flujos de trabajo del HMIS (descritos en detalle en la parte posterior de este documento)** | <p> </p><p><strong>Recomendación o requisito</strong></p> |
| ---------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| <p> </p><p><strong>HMISWF-1</strong></p> | Validar y guardar datos agregados.                                                            | <p> </p><p>Requisito</p>                                  |

## Requisitos funcionales del HMIS de OpenHIE

| <p> <strong></strong> </p><p>N.º</p>                                                | **Requisitos funcionales del HMIS**                                                                                                                                | **Recomendación o requisito**                                            |
| ----------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HMISF-1</strong></p> | Un HMIS debe actuar como un almacén de datos del sistema de salud integrado que puede ser utilizado para una mejor toma de decisiones dentro del sistema de salud. | <p> <strong></strong> </p><p> <strong></strong> </p><p>Requisito</p>     |
| <p> <strong></strong> </p><p><strong>HMISF-2</strong></p>                           | Un HMIS debe proporcionar mecanismos (preferiblemente basados en la web) para la introducción de datos.                                                            | <p> <strong></strong> </p><p>Recomendación</p>                           |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HMISF-3</strong></p> | Un HMIS debe proporcionar mecanismos para mejorar la calidad y validez de los datos (formularios inteligentes, reglas de validación, etc.).                        | <p> <strong></strong> </p><p> <strong></strong> </p><p>Recomendación</p> |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HMISF-4</strong></p> | Un HMIS debería proporcionar interfaces estándar para la importación de datos de otros sistemas (p. ej., ADX o FHIR).                                              | <p> <strong></strong> </p><p> <strong></strong> </p><p>Recomendación</p> |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HMISF-5</strong></p> | Un HMIS debe permitir el uso de una lista precisa de los instalaciones de salud y su distribución geográfica y administrativa.                                     | <p> <strong></strong> </p><p> <strong></strong> </p><p>Recomendación</p> |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HMISF-6</strong></p> | Un HMIS debe proporcionar interfaces para compartir la información de los instalaciones de salud con otros sistemas (registro de instalaciones).                   | <p> <strong></strong> </p><p> <strong></strong> </p><p>Recomendación</p> |

\


| <p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HMISF-7</strong></p> | <p> <strong></strong> </p><p>Para apoyar su función principal de uso de datos, un HMIS debería hacer lo siguiente:</p><p>·     Ser capaz de agregar y analizar más datos (p. ej., proporcionar un informe anual a partir de datos mensuales).</p><p>·     Un HMIS debe ofrecer una interfaz para consultar sus datos de forma flexible en diferentes dimensiones (API de análisis).</p><p>·     Un HMIS debe proporcionar visualizaciones gráficas personalizadas de los datos.</p> | <p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p> <strong></strong> </p><p>Recomendación</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
