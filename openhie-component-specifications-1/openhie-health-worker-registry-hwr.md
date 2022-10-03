# Registro de Trabajadores de la Salud (HWR) de OpenHIE

El Registro de Trabajadores de la Salud (Health Worker Registry, HWR) sirve como autoridad central para mantener las identidades únicas de los trabajadores de la salud dentro de un país. El Registro de Trabajadores de la Salud es una base de datos que contiene un conjunto mínimo de detalles de todos los trabajadores de la salud que trabajan tanto en el sector público como en el privado. Con múltiples y dispares fuentes de datos sobre los trabajadores de la salud, es una tarea compleja reunir y mantener una lista maestra y canónica de todos los trabajadores de la salud de un país. El registro de trabajadores de la salud pretende reducir la complejidad de esta tarea:

&#x20;

* Extraer el conjunto de datos mínimo de información sobre el personal de la salud de los distintos sistemas de datos de origen.
* Fusionar los sistemas de datos de origen en un registro autorizado de trabajadores de la salud de acuerdo con una política de gobernanza de datos.
* Permitir que los sistemas cliente consulten la información de los trabajadores de la salud.

&#x20;

Consulte también “Requisitos no funcionales

## Requisitos del flujo de trabajo del HWR de OpenHIE

Un [principio básico de la arquitectura de OpenHIE ](https://wiki.ohie.org/display/resources/Architectural%2BPrincipals)es permitir que los distintos servicios de infraestructura (como el HWR) sean intercambiables. Para apoyar esto, los [estándares y perfiles de OpenHIE ](https://wiki.ohie.org/display/documents/OpenHIE%2BStandards%2Band%2BProfiles)utilizados por el Registro de Trabajadores de la Salud se describen en los siguientes flujos de trabajo.

&#x20;Para ser un componente del HWR de OHIE, la aplicación del HWR debe ser capaz de soportar los flujos de trabajo de OHIE que se enumeran a continuación. Las implementaciones pueden admitir solo los flujos de trabajo necesarios para apoyar su caso de uso:\


| <p> </p><p>N.º</p>                     | **Flujos de trabajo del HWR (descritos en detalle en la parte posterior de este documento)** | <p> </p><p><strong>Recomendación o requisito</strong></p>      |
| -------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| <p> </p><p><strong>HWWF-1</strong></p> | Flujo de trabajo para consultar registros de trabajadores de la salud o de instalaciones.    | Requisito (debe admitirse una de las opciones HWWF-1 o HWWF-2) |
| <p> </p><p><strong>HWWF-2</strong></p> | Consulta del flujo de trabajo de los registros de los servicios de atención.                 | Requisito (debe admitirse una de las opciones HWWF-1 o HWWF-2) |
| **HWWF-3**                             | Buscar el flujo de trabajo de los servicios de atención.                                     | Recomendación                                                  |
| <p> </p><p><strong>HWWF-4</strong></p> | Solicitar actualizaciones de los servicios de atención.                                      | <p> </p><p>Requisito</p>                                       |

## Requisitos funcionales del HWR de OpenHIE



| <p> <strong></strong> </p><p><strong>N.º</strong></p>                              | <p> <strong></strong> </p><p><strong>Requisito funcional del HWR</strong></p>                                                                                    | **Recomendación o requisito**                                            |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HWRF-1</strong></p> | El sistema deberá permitir consultar los sistemas de datos de origen para actualizar los datos de los trabajadores de la salud.                                  | <p> <strong></strong> </p><p> <strong></strong> </p><p>Requisito</p>     |
| <p> <strong></strong> </p><p><strong>HWRF-2</strong></p>                           | El sistema deberá permitir conservar las actualizaciones recibidas de los sistemas de datos de origen.                                                           | <p> <strong></strong> </p><p>Requisito</p>                               |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HWRF-3</strong></p> | El sistema deberá permitir responder consultas sobre los datos de los trabajadores de la salud que se hayan almacenado.                                          | <p> <strong></strong> </p><p> <strong></strong> </p><p>Requisito</p>     |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HWRF-4</strong></p> | El sistema deberá ser capaz de enviar actualizaciones a los repositorios de datos anteriores (como un registro interconectado).                                  | <p> <strong></strong> </p><p> <strong></strong> </p><p>Recomendación</p> |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HWRF-5</strong></p> | El sistema debe apoyar la capacidad de mantener las versiones antiguas de los datos de los trabajadores de la salud cuando se han actualizado.                   | <p> <strong></strong> </p><p> <strong></strong> </p><p>Recomendación</p> |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>HWRF-6</strong></p> | <p>El sistema debe admitir la recopilación de datos para el siguiente conjunto de datos mínimo:</p><p>https://www.who.int/hrhstatistics/minimun_data_set/en/</p> | <p> <strong></strong> </p><p> <strong></strong> </p><p>Recomendación</p> |
| <p> </p><p><strong>HWRF-7</strong></p>                                             | El sistema debe contar con API flexibles basadas en estándares, basadas en CSD o mCSD                                                                            | <p> </p><p>Requisito</p>                                                 |
