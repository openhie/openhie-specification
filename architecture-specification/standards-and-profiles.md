# Estándares y Perfiles

## **Perfiles HIE**

Los siguientes son los perfiles de HIE en los que OpenHIE está trabajando para demostrar o ha demostrado que son compatibles con las implementaciones de referencia. Sin embargo, la arquitectura OpenHIE **no se limita a dar soporte a estos perfiles**.

| StanEstándar                                                                                                         | Propósito                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [ADX](http://wiki.ihe.net/index.php?title=Aggregate\_Data\_Exchange)                                                 | El **perfil de intercambio de datos agregados (ADX)** permite informes de salud pública interoperables de datos sanitarios agregados. ADX se utilizará típicamente para representar datos agregados informados de forma rutinaria, como los numeradores y denominadores que se pueden utilizar en la construcción de indicadores de salud pública[. Consulte Flujos de trabajo de generación de informes agregados](../introduction/aggregate-reporting-workflows/) para obtener más información sobre cómo se utiliza.                                                                                                                                                                                             |
| [ADX-COVID](https://github.com/IHE/QRPH.ADX.COVID19)                                                                 | El perfil ADX **(Intercambio de datos agregados)** ofrece a los socios de intercambio de datos una forma para precisar una Definición de estructura de datos y el esquema normativo asociado del mensaje de datos para el informe de un indicador en particular. [Consulte Flujos de trabajo de generación de informes agregados](../introduction/aggregate-reporting-workflows/) para obtener más información sobre cómo se utiliza.                                                                                                                                                                                                                                                                               |
| [ADX-HIV](https://wiki.ihe.net/index.php/Aggregate\_Data\_Exchange\_-\_HIV)                                          | El perfil ADX **(Intercambio de datos agregados)** ofrece a los socios de intercambio de datos una forma para precisar una Definición de estructura de datos y el esquema normativo asociado del mensaje de datos para un informe de indicador en particular. Para fomentar una mayor adopción, el perfil de Intercambio de datos agregados -HIV (ADX-HIV) aprovecha la versión 2.1 del perfil ADX, que actualmente se publica para la implementación de prueba, para desarrollar una especificación de contenido específicamente para el VIH. [Consulte Flujos de trabajo de generación de informes agregados](../introduction/aggregate-reporting-workflows/) para obtener más información sobre cómo se utiliza. |
| [APS](http://wiki.ihe.net/index.php?title=Antepartum\_Care\_Summary\_Profile)                                        | El documento **APS** es un resumen médico y hereda todas las restricciones de encabezado de los resúmenes médicos.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| [ATNA](http://wiki.ihe.net/index.php?title=Audit\_Trail\_and\_Node\_Authentication)                                  | El Perfil de Integración de **Autenticación de Nodos y Registro de Auditoría (ATNA)** establece medidas de seguridad que, junto con la Política y los Procedimientos de Seguridad, brindan confidencialidad a la información del paciente, integridad de los datos y la cuenta del usuario.                                                                                                                                                                                                                                                                                                                                                                                                                         |
| [CSD](ftp://ftp.ihe.net/DocumentPublication/CurrentPublished/ITInfrastructure/IHE\_ITI\_Suppl\_CSD.pdf)              | El perfil **Descubrimiento de Servicios de Asistencia (CSD)** admite consultas en directorios relacionados que contienen datos sobre: organizaciones, instalaciones, servicios y proveedores. También se admiten consultas contra un servicio "libre/ocupado" opcional; esta información de libre/ocupado apoyaría el desarrollo de una lista de intervalos de tiempo programables para proveedores o servicios en instalaciones específicas. [Consulte los flujos de trabajo de Descubrimiento de Servicios de Asistencia](../introduction/care-services-discovery/) para obtener más información sobre cómo se utiliza.                                                                                           |
| [CT](http://wiki.ihe.net/index.php?title=Consistent\_Time)                                                           | El **tiempo compatible (CT)** permite sincronizar los relojes del sistema y las marcas de tiempo de las computadoras en una red (error promedio de menos de 1 segundo).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| [mACM](http://wiki.ihe.net/index.php?title=Mobile\_Alert\_Communication\_Management\(mACM\))                         | **La gestión de Comunicación de Alertas para dispositivos móviles** envía alertas unidireccionales a trabajadores de la salud y beneficiarios del sistema de salud (clientes). [Consulte la sección Envío de Alertas/ recordatorios o información de este documento](../introduction/alerting-sending-reminders-or-information/) para obtener más información sobre cómo se utiliza.                                                                                                                                                                                                                                                                                                                                |
| [mADX](https://wiki.ihe.net/index.php/Mobile\_Aggregate\_Data\_Exchange\_\(mADX\))                                   | Estándar FHIR emergente para el intercambio de datos agregados. [Consulte Flujos de trabajo de generación de informes agregados](../introduction/aggregate-reporting-workflows/) para obtener más información sobre cómo se utiliza.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| [mCSD](https://www.ihe.net/uploadedFiles/Documents/ITI/IHE\_ITI\_Suppl\_mCSD.pdf)                                    | El perfil de **Descubrimiento de Servicios de Asistencia para dispositivos móviles** admite consultas en directorios relacionados que contienen datos sobre: organizaciones, instalaciones, servicios y proveedores. Basado en HL7 FHIR. [Consulte Descubrimiento de Servicios de Asistencia](../introduction/care-services-discovery/) para obtener más información sobre cómo se utiliza.                                                                                                                                                                                                                                                                                                                         |
| [MHD](http://wiki.ihe.net/index.php/Mobile\_access\_to\_Health\_Documents\_\(MHD\))                                  | El perfil de **Acceso a Documentos Sanitarios** **para dispositivos móviles** define una interfaz HTTP simple para un entorno similar a XDS. El perfil MHD está diseñado para cualquier sistema que prefiera la tecnología HTTP RESTful simplificada en lugar de la tecnología más robusta utilizada en XDS. Define transacciones para a) enviar un conjunto de documentos y metadatos desde el dispositivo móvil a un receptor de documentos, b) encontrar los metadatos del conjunto de envío de documentos en función de los parámetros de consulta; c) encontrar entradas de documentos que contengan metadatos basados ​​en parámetros de consulta, y d) recuperar una copia de un documento específico.       |
| [MHDS](https://wiki.ihe.net/index.php/Mobile\_Health\_Document\_Sharing\_\(MHDS\))                                   | El perfil de **Intercambio de documentos sanitarios para dispositivos móviles** especifica cómo las comunidades pueden usar una colección de perfiles de HIE para intercambiar información de salud. Estos perfiles HIE incluyen soporte para la identificación de pacientes, ubicación y recuperación de documentos sanitarios, directorios de proveedores y la protección de la privacidad y la seguridad. MHDS muestra cómo varios perfiles HIE trabajan juntos para proporcionar un enfoque interoperable basado en estándares para el intercambio de información sobre la salud comunitaria.                                                                                                                   |
| [PDQ](http://wiki.ihe.net/index.php?title=Patient\_Demographics\_Query)                                              | El perfil de integración de **Consulta de datos demográficos del paciente (PDQ)** permite que las aplicaciones consulten un servidor central de información del paciente y recuperen la información demográfica de un paciente.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| [PDQm](http://wiki.ihe.net/index.php?title=Patient\_Demographics\_Query\_for\_Mobile\_\(PDQm\))                      | El perfil de **Consulta de datos demográficos de pacientes para dispositivos móviles (PDQm)** define una interfaz RESTful ligera para un proveedor de datos demográficos de pacientes que aprovecha las tecnologías fácilmente disponibles para aplicaciones móviles y aplicaciones ligeras basadas en navegador. La funcionalidad es idéntica al perfil PDQ descrito en ITI TF-1:8.                                                                                                                                                                                                                                                                                                                                |
| [PIX](http://wiki.ihe.net/index.php?title=Patient\_Identifier\_Cross-Referencing)                                    | <p>El perfil de integración de <strong>referencias cruzadas de identificadores de pacientes (PIX)</strong> admite las referencias cruzadas de varios dominios de identificadores de pacientes mediante:</p><ul><li>La transmisión de información de identidad del paciente desde una fuente de identidad al Administrador de referencias cruzadas de identificadores de pacientes.</li><li>Brindar la capacidad de acceder a la(s) lista(s) de identificadores de pacientes con referencias cruzadas ya sea a través de una consulta/respuesta o mediante una notificación de actualizació</li></ul>                                                                                                                |
| [PMIR](https://wiki.ihe.net/index.php/Patient\_Master\_Identity\_Registry\_\(PMIR\))                                 | El perfil del **Registro de identidad principal del paciente (PMIR)** admite la creación, actualización y desuso de la información de identidad principal del paciente sobre un tema de atención, así como la suscripción a cambios en la identidad principal del paciente, utilizando los recursos estándar HL7 FHIR y las transacciones RESTful.                                                                                                                                                                                                                                                                                                                                                                  |
| [SVCM](https://wiki.ihe.net/index.php/Sharing\_Valuesets,\_Codes\_and\_Maps\_\(SVCM\))                               | **S**Los **Valores establecidos, Sistemas de codificación y mapas compartidos** proporcionan transacciones básicas asociadas con los servicios de terminología. Las transacciones se basan en las operaciones de los recursos CodeSystem FHIR, ValueSet y ConceptMap. SVCM se encuentra actualmente en estado de implementación de prueba. [Consulte el servicio de terminología de los flujos de trabajo](../introduction/terminology-service-workflow/).                                                                                                                                                                                                                                                          |
| [XDS.b](http://wiki.ihe.net/index.php/XDS.b\_Implementation)[ ](http://wiki.ihe.net/index.php/XDS.b\_Implementation) | El **Intercambio de documentos entre empresas (XDS.b)** se centra en proporcionar una especificación basada en estándares para administrar el intercambio de documentos entre cualquier empresa de atención médica, desde un consultorio médico privado hasta una clínica, un centro de cuidados intensivos para pacientes hospitalizados y sistemas de registros personales de salud.                                                                                                                                                                                                                                                                                                                              |

{% hint style="info" %}
Para obtener documentación sobre cuántos de estos perfiles funcionan juntos en un HIE, consulte [MHDS](https://wiki.ihe.net/index.php/Mobile\_Health\_Document\_Sharing\_\(MHDS\)), [el informe técnico de HIE](https://profiles.ihe.net/ITI/HIE-Whitepaper/index.html) y la sección de especificación de flujo de [trabajo (intercambio) de esta especificación](../introduction/).
{% endhint %}
