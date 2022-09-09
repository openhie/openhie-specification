# Arquitectura

## **Resumen** <a href="#resumen" id="resumen"></a>

Un Intercambio de Información Sanitaria (HIE), la infraestructura compartida en el gran recuadro gris del Diagrama de Arquitectura de OpenHIE, hace posible el intercambio de datos de salud entre sistemas de información. Al igual que un traductor universal, un HIE normaliza los datos y asegura la transmisión de la información sanitaria a través de las bases de datos, entre instalaciones y a través de regiones o países.La arquitectura de OpenHIE está formada por componentes de software, todos ellos interactuando/interoperando para garantizar que la información sanitaria de varios sistemas de puntos de servicio se reúna en un intercambio de información sanitaria. Para lograrlo, el intercambio normaliza el contexto en el que se crea la información sanitaria a través de múltiples dimensiones, entre ellas

1. Quién ha recibido los servicios sanitarios
2. Quién prestó los servicios
3. En dónde se recibieron los servicios
4. Qué cuidados y servicios concretos se recibieron
5. Qué productos pueden haber intervenido en el tratamiento
6. Quién tiene la responsabilidad financiera

Esta separación de cuestiones apoya la calidad, la seguridad y la continuidad de la atención, y facilita el uso adecuado de la información necesaria para la salud de la población y el cálculo de métricas.Diagrama de la arquitectura de OpenHIE​



## Diagrama de arquitectura OpenHIE

<figure><img src="https://lh3.googleusercontent.com/khEPGMvObLh9YEZ26N4k6_ahTJ6VSkkOzOEfRkPMV8v9QvE2wR0fI44-fpjTglpig8hplLr9dfFZ5r6ZQQC-cKxBVV2c1W_U4YQZ_yY21_jWfkbSiJP03B97l-0L8aAb9Uv_gXBI52toGkLzGXjjhF3PU92GcSGloIMCF5tn9AgUuyqlTNIig_NBA1sJ0dfHbHem1Q" alt=""><figcaption></figcaption></figure>

### Descripciones de los componentes de la arquitectura <a href="#descripciones-de-los-componentes-de-la-arquitectura" id="descripciones-de-los-componentes-de-la-arquitectura"></a>

#### Servicios de dominio empresarial <a href="#servicios-de-dominio-empresarial" id="servicios-de-dominio-empresarial"></a>

Los Servicios de Dominio Empresarial son componentes de Intercambio de Salud que están diseñados para apoyar dominios de negocio específicos del sistema de salud y tendrían el potencial de combinar datos de Intercambio Sanitario de múltiples sistemas de puntos de atención.

1. Servicio de Gestión Logística (LMIS) - Un Sistema de Gestión Logística (LMIS) es un sistema informático que desempeña un papel central pues permite la visibilidad de los productos y la gestión operativa de la cadena de suministro de área amplia. Por lo general, los productos de esta cadena de suministro están relacionados con la salud, la organización que patrocina el sistema es un departamento o agencia gubernamental dependiente de un ministerio de salud y la operación se lleva a cabo a escala de toda una región o incluso de todo un país. Un LMIS suele tender un puente entre las operaciones de la cadena de salud y las de la cadena de suministro al permitir los flujos de trabajo de reabastecimiento para las ubicaciones clínicas y los programas verticales dirigidos a las familias de productos, así como al interconectarse con los sistemas informáticos de los proveedores para garantizar que el proceso de reabastecimiento se cumpla según sea necesario. Determinadas herramientas del LMIS pueden tener capacidades adicionales que mejoren estos flujos de trabajo de reabastecimiento y/o añadan madurez a la operación más amplia de la cadena de suministro.
2. Un Registro de Salud Compartido (SHR) es un repositorio que contiene la versión normalizada de los contenidos creados dentro de la comunidad, después de haber sido validados con cada uno de los registros anteriores. Es una colección de registros centrados en la persona para pacientes con información en el intercambio. Véase también: ¿Qué constituye un SHR de OpenHIE?
3. Un Servicio de Información de Gestión de la Salud (HMIS) almacena los datos agregados de atención sanitaria recogidos de forma rutinaria y facilita su análisis con el objetivo de mejorar la calidad de los servicios de salud. Véase también: ¿Qué constituye un HMIS de OpenHIE?
4. El Servicio de Finanzas y Seguros almacena, clasifica y facilita la administración de los reclamos centralizados y los datos financieros relacionados con la prestación de atención a los pacientes dentro del HIE. El servicio recibe los reclamos/datos financieros de las aplicaciones de los Puntos de Servicio (incluidas las aplicaciones de finanzas que actúan como interfaz de los puntos de servicio fuera de otros sistemas de PoS) y selecciona la gestión de los mismos.

#### Servicios de registro <a href="#servicios-de-registro" id="servicios-de-registro"></a>

Los Servicios de Registro son Componentes de Intercambio de Salud que están diseñados para apoyar los registros con datos que son utilizados por otros componentes de Intercambio de Información Sanitaria.

1. Un Servicio de Terminología sirve como autoridad central para identificar de forma única las actividades clínicas que ocurren dentro del proceso de prestación de cuidados mediante el mantenimiento de un conjunto de términos asignado a estándares internacionales como ICD-10, LOINC, SNOMED y otros - "¿Qué?". Véase también: ¿Qué es un Servicio de Terminología OpenHIE?
2. Un Índice Maestro de Pacientes de la Empresa (EMPI), o Registro de Clientes gestiona la identidad única de los ciudadanos que reciben servicios sanitarios en el país - "Para quién". Véase también: ¿Qué es un CR de OpenHIE?
3. Un Registro de Centros Sanitarios sirve como autoridad central para identificar de forma única todos los lugares donde se administran servicios sanitarios dentro del país - "¿Dónde?".  Véase también: ¿En qué consiste un Registro de Centros de OpenHIE?
4. Un Registro de Trabajadores de la Salud es la autoridad central para mantener las identidades únicas de los proveedores de salud dentro del país - "¿Por quién?" . Véase también: ¿En qué consiste un Registro de Trabajadores de la Salud?
5. Catálogo de Productos - El Catálogo de Productos sirve como el lugar de verificación de lo que es un Producto dentro de un HIE. Obtiene la información para esta función a través de dos medios esperados: 1) como resultado continuo de un proceso de gestión de datos maestros para definir y categorizar adecuadamente los productos médicos y 2) como datos derivados de la definición y categorización adecuadas de los productos médicos (por ejemplo, GS1 GDSN).

### Capa de Servicios de Interoperabilidad <a href="#capa-de-servicios-de-interoperabilidad" id="capa-de-servicios-de-interoperabilidad"></a>

1. **Autenticación** - Verificación de las credenciales de los sistemas que envían mensajes a la capa de interoperabilidad.
2. **Servicio de interconexión** - Servicio para vincular a los trabajadores sanitarios con las instalaciones.
3. La Capa de Interoperabilidad Sanitaria recibe todas las comunicaciones de los servicios externos dentro de una geografía sanitaria y organiza el procesamiento de mensajes entre los sistemas externos y la capa de componentes de OpenHIE. Véase también: ¿Qué es una Capa de Interoperabilidad de OpenHIE?
4. **Mapeo de Entidades** - Proceso de emparejamiento de entidades para vincular registros duplicados. Se puede utilizar para emparejar entidades con el fin de determinar si hay coincidencias potenciales dentro de una única lista o a través de dos listas. Esta función puede utilizarse con cualquier entidad, pero se ha utilizado con mayor frecuencia con los registros demográficos de los pacientes para vincular los registros de un paciente individual de sistemas dispares o para emparejar los registros de las instalaciones en diferentes sistemas.

### Punto de servicio <a href="#punto-de-servicio" id="punto-de-servicio"></a>

Las aplicaciones de Punto de Servicio, como el sistema de Historia Clínica Electrónica (EMR) OpenMRS y la aplicación RapidSMS mHealth, son utilizadas por los médicos y por los trabajadores sanitarios a nivel comunitario para acceder a y actualizar la información sanitaria compartida centrada en la persona de un paciente y para registrar las transacciones sanitarias. Comparten los datos interactuando con el Intercambio de Información Sanitaria representado en el cuadro gris más grande.\
\
