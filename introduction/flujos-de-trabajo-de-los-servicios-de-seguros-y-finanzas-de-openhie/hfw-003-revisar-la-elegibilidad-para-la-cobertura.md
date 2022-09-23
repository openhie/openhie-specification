# HFW-003: Revisar la elegibilidad para la cobertura

Este flujo de trabajo se puede usar para verificar si un paciente está inscrito en la cobertura y, opcionalmente, examinar si se pueden aplicar servicios específicos.

Ejemplo de casos de uso:

•  Si una madre se presenta en un hospital, este flujo de trabajo se puede utilizar para determinar si está inscrita en el esquema de atención posnatal de Salud Materno Infantil (Maternal and Child Health, MCH) del Ministerio de Salud (Ministry of Health, MoH).

•  Un paciente es diagnosticado con cáncer y necesita quimioterapia. El hospital pregunta sobre la cobertura de la quimioterapia.



| <p> </p><p> </p><p> </p><p>Madurez del flujo de trabajo</p> | <p> </p><p><img src="file:///Users/dtrefun/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image001.jpg" alt=""></p><p>Recién definido</p><p> </p><p>•     El flujo de trabajo está definido y aprobado por la ARB.</p><p> </p><p>•     Las implementaciones iniciales están en marcha.</p>                                                                                                                                                                                                                                                                                                                     |
| ----------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p> </p><p> </p><p>Estándares</p>                           | <p> </p><p>•     Módulo de finanzas HL7 FHIR: <a href="http://hl7.org/fhir/financial">http://hl7.org/fhir/financial­</a> module.html</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Supuestos y prerrequisitos                                  | Ninguno                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Actores                                                     | <p>•     PoS: el sistema de punto de servicio que captura un encuentro clínico con un paciente es responsable de enviar este encuentro al HIE.</p><p>•     IOL: media en las transacciones entre el sistema PoS y los servicios de infraestructura para facilitar la interoperabilidad.</p><p>•     CR: fuente de la verdad para los detalles demográficos e identificadores del paciente. Se puede consultar utilizando un identificador para encontrar el identificador de la empresa para una persona en particular.</p><p>•     FIS: sistema de financiamiento y seguros que maneja los datos de los beneficiarios y sus coberturas.</p> |
| <p> </p><p>Validaciones</p>                                 | La IOL o el PoS debe validar los recursos que se envían de FHIR.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

### **Descripción de la interacción**

![](https://lh6.googleusercontent.com/nGHZHLc5wa6NUe9utNSFkDWHIl2zaAq88pA-E1anht-t5lIiiZt-aF\_uOfuyYktkd4N2BvAs6Hkcv\_tHVA50L\_0HtSFIfwL8Y09bbodxBCrqdov66xPX\_s4DREqOsGVI8Wbhb9-0)

#### Código del recurso

(enlace al texto permanente en [https://www.websequencediagrams.com/](https://www.websequencediagrams.com))

```
title HFW-003: Check Coverage Eligibility
participant PoS
participant IOL
participant FIS



opt Get code lists for Medical Procedures & Items
	PoS -> IOL: [1] Submit Medical Procedures & Items Query
	IOL -> FIS: [2] Forward query
	FIS -> FIS: [3] Process query
	FIS -> IOL: [4] Return  Medical Procedures & Items
	IOL -> PoS: [5] Forward Medical Procedures & Items
end opt
 

PoS -> IOL: [6] Submit Coverage Eligibility Query
IOL -> FIS: [7] Forward Query
FIS -> FIS: [8] Process Insuree Query
FIS -> FIS: [9] Process Policy Query
FIS -> IOL: [10] Return Coverage Eligibility Result
IOL -> PoS: [11] Forward Coverage Eligibility Result
```

### **Detalles técnicos**



| Ref                                      | Interacción                                                                     | Punto final                                | Datos                                                                                   | Especificaciones de la transacción                                                                                                                                                |
| ---------------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------ | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p> </p><p>1</p>                         | Envío de la consulta de procedimientos y artículos médicos                      | <p> </p><p>IOL</p>                         |                                                                                         |                                                                                                                                                                                   |
| <p> </p><p> </p><p> </p><p> </p><p>2</p> | <p> </p><p> </p><p> </p><p> </p><p>Reenviar consulta</p>                        | <p> </p><p> </p><p> </p><p> </p><p>FIS</p> | <p> </p><p> </p><p> </p><p>FHIR</p><p>de la actividad de FHIR, medicamentos de FHIR</p> | <p> </p><p> </p><p><a href="http://hl7.org/fhir">http://hl7.org/fhir</a> R4/activitydefiniti on.html <a href="http://hl7.org/fhir/">http://hl7.org/fhir/</a> R4/medication.ht</p> |
| 3                                        | Proceso de consulta                                                             | interno                                    |                                                                                         |                                                                                                                                                                                   |
| <p> </p><p> </p><p> </p><p> </p><p>4</p> | <p> </p><p> </p><p> </p><p>Devolución de procedimientos y artículos médicos</p> | <p> </p><p> </p><p> </p><p> </p><p>IOL</p> | <p> </p><p> </p><p> </p><p>FHIR</p><p>de la actividad de FHIR, medicamentos de FHIR</p> | <p> </p><p> </p><p><a href="http://hl7.org/fhir/">http://hl7.org/fhir/</a> R4/activitydefiniti on.html <a href="http://hl7.org/fhir">http://hl7.org/fhir</a> R4/medication.h</p>  |
| <p> </p><p> </p><p>5</p>                 | Reenvío de procedimientos y artículos médicos                                   | <p> </p><p> </p><p>POS</p>                 |                                                                                         |                                                                                                                                                                                   |
| <p> </p><p>6</p>                         | <p>Enviar cobertura</p><p> </p><p>E ioihi itv Ouerv</p><p> </p>                 | <p> </p><p>IOL</p>                         |                                                                                         |                                                                                                                                                                                   |
| <p> </p><p> </p><p>7</p>                 | Reenviar consulta                                                               | <p> </p><p>FIS</p>                         | <p>FHIR</p><p>CoverageEligibilityRequest</p><p> </p>                                    | <p>http://hl7.org/fhir/</p><p>R4/coverageeligi</p><p> </p><p>bilityrequest. html</p>                                                                                              |
| <p> </p><p> </p><p>8</p>                 | Consulta del proceso del seguro                                                 | <p> </p><p>interno</p>                     |                                                                                         |                                                                                                                                                                                   |
| <p> </p><p> </p><p>9</p>                 | Consulta sobre las políticas del proceso                                        | <p> </p><p>interno</p>                     |                                                                                         |                                                                                                                                                                                   |
| <p> </p><p> </p><p>1</p>                 | Devolución de los resultados de la elegibilidad para la cobertura               | <p> </p><p>IOL</p>                         | <p>FHIR</p><p>CoverageEligibilityResponse</p>                                           | <p>http://hl7.org/fhir/R4/coverageeligi</p><p>bilityresponse.html</p>                                                                                                             |
| <p> </p><p> </p><p>1</p>                 | Reenvío de los resultados de elegibilidad para la cobertura                     | <p> </p><p>POS</p>                         |                                                                                         |                                                                                                                                                                                   |
