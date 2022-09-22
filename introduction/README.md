# Especificaciones del flujo de trabajo (intercambio)

Los flujos de trabajo de OpenHIE (OHIE) son los patrones de intercambio de datos técnicos para compartir datos de salud entre uno o más de los componentes de la arquitectura de OpenHIE u otros sistemas de información de salud. Como se especifica en el proceso documentado anteriormente, la Junta de Revisión de Arquitectura de OpenHIE ha examinado y aprobado los flujos de trabajo de OpenHIE. El propósito de esta sección es documentar las especificaciones del flujo de trabajo para OpenHIE. Se están creando nuevos flujos de trabajo y es posible que aún no se hayan incorporado estándares adicionales como los Recursos Rápidos de Interoperabilidad de Atención Médica (Fast Healthcare Interoperability Resources, FHIR) y este tipo de trabajo en progreso se puede encontrar en el wiki de OpenHIE. Además, está invitado a unirse a nuestros procesos y contribuir con nuevos flujos de trabajo para el próximo lanzamiento.

&#x20;

Para cada flujo de trabajo se documenta lo siguiente:

* Madurez. La madurez de cada flujo de trabajo se documenta de manera subjetiva con base en los siguientes factores:
  * El flujo de trabajo está definido y aprobado por la Junta de Revisión de Arquitectura (Architecture Review Board, ARB).The workflow is supported by standards
  * El flujo de trabajo admite estándares.
  * &#x20;La madurez de los estándares o perfiles subyacentes.
  * El número de implementaciones.&#x20;
* Estándares. Perfiles de Integrating the Healthcare Enterprise (IHE) que son los componentes básicos de los flujos de trabajo de OpenHIE. Estos perfiles de IHE representan las descripciones comprobables de conformidad de cómo deben comportarse los actores en un intercambio de datos interoperable. La madurez de los estándares de los FHIR subyacentes, en sí mismos, se identifica en la primera página de la especificación del perfil de IHE. La lista de recursos de los FHIR se puede mostrar y ordenar por madurez; esta lista se encuentra aquí: https://[www.hl7.org/fhir/resourcelist.html. ](http://www.hl7.org/fhir/resourcelist.html)(Los niveles de madurez de los FHIR se definen aquí: https://[www.hl7.org/fhir/versions.html#maturity).](http://www.hl7.org/fhir/versions.html#maturity\))
* Supuestos y prerrequisitos. Condiciones que se espera que existan para respaldar el flujo de trabajo.
* Actores. Sistemas o componentes del Intercambios de Información de Salud (Health Information Exchange, HIE) que tienen roles en el proceso de intercambio de datos que se especifica.
* Diagrama de interacción. La descripción visual de cómo se mueven los datos entre sistemas.
* Pasos del diagrama de interacción. Detalles que explican los pasos del diagrama de interacción &#x20;

