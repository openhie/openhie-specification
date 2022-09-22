# Flujo de trabajo para la solicitud de actualizaciones de servicios de atención

El flujo de trabajo para una aplicación de punto de servicio para consultar un registro de servicios de atención o directorio para actualizar a los trabajadores de la salud, instalaciones, organizaciones o los servicios proporcionados por cada uno.



| <p> </p><p> </p><p> </p><p> </p><p> </p><p><strong>Madurez del flujo de trabajo</strong></p> | <p> </p><p> </p><p> </p><p> </p><p> </p><p><strong>Madurez</strong></p><p><img src="file:///Users/dtrefun/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image001.png" alt=""></p> | <p> </p><p> </p><p>•     El flujo de trabajo está definido y aprobado por la ARB.</p><p>•     El flujo de trabajo admite el estándar emergente mCSD de IHE</p>                                                                                                      |
| -------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p> </p><p> </p><p> </p><p>Estándares*</p>                                                   |                                                                                                                                                                                                                  | <p>Descubrir servicios de atención móviles (mCDS):</p><p>ftp://ftp.ihe.net/DocumentPublica tion/CurrentPublished/lTlnfrastru cture/lHE_ITI_Suppl_mCSD.pd</p>                                                                                                        |
| <p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>Supuestos y prerrequisitos</p>    |                                                                                                                                                                                                                  | <p> </p><p>Un registro de servicios de atención deberá contar con uno o más de los siguientes recursos:</p><p> </p><p>•     Ubicación</p><p>•     Profesión y rol profesional</p><p>•     Organización</p><p>•     Servicios de atención médica</p>                 |
| <p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>Actores</p>                               |                                                                                                                                                                                                                  | <p> </p><p> </p><p>•     ILR: Registros Interconectados, actualización de servicios de atención del consumidor de mCSD</p><p>•     CSR: Cualquier registro de servicios de atención (p. ej., HWR o FR) mCSD Proveedor de actualización de servicios de atención</p> |

## Descripción de la interacción

La siguiente es una descripción de los pasos de la interacción.

![](https://lh5.googleusercontent.com/Qo99bmR5cItDA89ePqPqp8OUxcZx6pydhwRUhP64aIOCzmMYLqIQTWvJLXUhV1SQ7L5VsjVr86SW30sD9zWu2EHVLRHwLw7K9-BquP4HvSRuxOQAT\_kZLlx0IuEerASdaw)



| N.º                              | **Interacción**                                                                  | **Datos/notas**                                                                                                            | **Opciones de transacciones**                                                         |
| -------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| <p> </p><p> </p><p> </p><p>1</p> | <p> </p><p> </p><p>Solicitud de actualizaciones de los servicios de atención</p> | Solicitud HTTP GET con parámetros de datos opcionales. Puede ser para cualquier recurso que admite.                        | <p> </p><p> </p><p>[ITI-91] Solicitud de actualizaciones de servicios de atención</p> |
| <p> </p><p> </p><p> </p><p>2</p> | <p> </p><p> </p><p>Devolver actualizaciones de servicios de atención</p>         | Respuesta HTTP con paquete FHIR de recursos coincidentes o un error si una solicitud no es válida o un error del servidor. | <p> </p><p> </p><p>[ITI-91] Solicitud de actualizaciones de servicios de atención</p> |
