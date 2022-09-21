# Flujo de trabajo de la búsqueda de servicios de atención

## El flujo de trabajo para una aplicación de punto de servicio para consultar el registro de servicios de atención para trabajadores de la salud, instalaciones, organizaciones o los servicios proporcionados por cada uno.

El flujo de trabajo para una aplicación de punto de servicio para consultar el registro de servicios de atención para trabajadores de la salud, instalaciones, organizaciones o los servicios proporcionados por cada uno.

| <p> </p><p> </p><p>Estándares*</p>                                                | **Descubrir servicios de atención móviles (mCSD): ftp:// ftp.ihe.net/DocumentPublication/CurrentPu blished/lTlnfrastructure/ IHE\_ITI\_Suppl\_mCSD.pdf**                                                                                                    |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>Supuestos y prerrequisitos</p> | <p> </p><p> </p><p>Un registro de servicios de atención deberá contar con uno o más de los siguientes recursos:</p><p> </p><p>•     Ubicación</p><p>•     Profesión y rol profesional</p><p>•     Organización</p><p>•     Servicios de atención médica</p> |
| <p> </p><p> </p><p> </p><p> </p><p>Actores</p>                                    | <p> </p><p> </p><p>•     Aplicación de punto de servicio (PoS), consumidor selectivo de servicios de atención de mCSD</p><p>•     ILR lnfoMan: Registros Interconectados, Servicios de atención selectivos del proveedor de mCSD</p>                        |

## Descripción de la interacción

La siguiente es una descripción de los pasos de la interacción.

![](https://lh3.googleusercontent.com/02eui3Y7oh1OzSYl2zzilg7gZfX8pEfJfvw2tNmvrFZg3TRmzjGsJmSFx5y3xqzRRamwKxJOoM2Z36SBgEmwy1fQ3yc-BAsevaBPw5ppor75EZIjDHTPQhQ3FTXwoKfkPQ)



| N.º                              | **Interacción**                                                                | **Datos/notas**                                                                                                            | **Opciones de transacciones**                                                   |
| -------------------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| <p> </p><p> </p><p> </p><p>1</p> | <p> </p><p> </p><p>[ITI-90] Búsqueda de servicios de atención coincidentes</p> | Solicitud HTTP GET con parámetros de consulta opcionales. Puede ser para cualquier recurso que admite.                     | <p> </p><p> </p><p>[ITI-90] Solicitud de servicios de atención coincidentes</p> |
| <p> </p><p> </p><p> </p><p>2</p> | <p> </p><p> </p><p>Devolver servicios de atención coincidentes</p>             | Respuesta HTTP con paquete FHIR de recursos coincidentes o un error si una solicitud no es válida o un error del servidor. | <p> </p><p> </p><p>[ITI-90] Solicitud de servicios de atención coincidentes</p> |

## ****
