# Consulta de mapas conceptuales

Esta transacción permite que un PoS, o cualquier componente de OHIE, acceda a información terminológica en el servicio de terminología para consultar los mapas conceptuales. Un ejemplo típico sería solicitar el conjunto de mapas conceptuales cuyo sistema de códigos objetivo es SNOMED CT. El mapeo se requiere con frecuencia cuando los datos de los pacientes se recopilan utilizando conceptos/códigos de un sistema de códigos, pero los datos deben informarse o agregarse, por ejemplo, para apoyar la toma de decisiones, en un sistema de códigos diferente. El conjunto de dichos conceptos asociados, generalmente para un caso de uso específico, se almacena en el Servicio de terminología en un recurso FHIR llamado mapa conceptual.

Tanto los sistemas externos como los internos del HIE pueden realizar esta transacción directamente con el TS. El siguiente diagrama de secuencia muestra los pasos que ocurren para un sistema que usa esta transacción.

&#x20;

1\. Consulta de mapas conceptuales: ¿Cuáles mapas conceptuales tienen un objetivo de mapa de "SNOMED CT"?



| <p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p><strong>Madurez del flujo de trabajo</strong></p> | <p> </p><p> </p><p> </p><p> </p><p> </p><p><img src="file:///Users/dtrefun/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image001.jpg" alt="Shape

Description automatically generated"></p><p><strong>Maduro</strong></p> | <p> </p><p> </p><p>•     <strong>Existen una o más implementaciones OpenHIE de este flujo de trabajo en uno o más países</strong></p><p>•     <strong>El flujo de trabajo está definido y aprobado por la ARB</strong></p><p>•     <strong>El flujo de trabajo admite estándares maduros</strong></p> |
| ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>Estándares*</p>                                   |                                                                                                                                                                                                                                                           | <p> </p><p> </p><p>•     Existen una o más implementaciones OpenHIE de este flujo de trabajo en uno o más países.</p><p>•     El flujo de trabajo está definido y aprobado por la ARB.</p><p>•     El flujo de trabajo admite estándares maduros</p>                                                  |
| <p> </p><p>Supuestos y prerrequisitos</p>                                                                    |                                                                                                                                                                                                                                                           | Los mapas conceptuales necesarios se han cargado previamente en el servicio de terminología.                                                                                                                                                                                                          |
| <p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>Actores</p>                                       |                                                                                                                                                                                                                                                           | <p> </p><p> </p><p>•     PoS: el sistema de punto de servicio u otro componente de HIE que se requiera para los mapas conceptuales.</p><p>•     TS: almacena la versión oficial seleccionada de los mapas conceptuales para el sistema de salud.</p>                                                  |

## Descripción de la interacción&#x20;

La siguiente es una descripción de los pasos de la interacción.

![](https://lh4.googleusercontent.com/lMBBRqFL2VgXeCrFBOPH-K-sDVo4hHqwW7gP7wxjyYAwbDHAITnWIGb3eddt6CQDVPCGPq3V56kCGENMV17f0WjgWxJ7R-XWpAX\_l2nKoEGMr-\_GDoPEd927PHERFR27QQ)



| N.º              | Interacción                                                | Datos                                                                           | Opciones de transacciones                            |
| ---------------- | ---------------------------------------------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------------- |
|                  |                                                            | La solicitud de búsqueda                                                        |                                                      |
|                  |                                                            | de mapas conceptuales                                                           |                                                      |
| 1                | <p>Solicitud de consulta</p><p>de mapas conceptuales</p>   | <p>se activa mediante un PoS</p><p>u otro componente de HIE.</p>                | <p>Recurso de mapa conceptual</p><p>de FHIR</p>      |
|                  |                                                            | Entrada: un conjunto de parámetros                                              |                                                      |
|                  |                                                            | de búsqueda de FHIR.                                                            |                                                      |
|                  |                                                            | La respuesta se devuelve                                                        |                                                      |
|                  |                                                            | al sistema que hizo                                                             |                                                      |
| <p> </p><p>2</p> | <p> </p><p>Respuesta de consulta de mapas conceptuales</p> | <p>la solicitud.</p><p>Salida: un paquete de recursos de mapas conceptuales</p> | <p> </p><p>Recurso de mapas conceptuales de FHIR</p> |
|                  |                                                            | que satisfagan                                                                  |                                                      |
|                  |                                                            | los parámetros de búsqueda de FHIR.                                             |                                                      |

##
