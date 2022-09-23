# HFW-005: Seguimiento a la reclamación



| <p> </p><p>Madurez del flujo de trabajo</p>                                    | <p>Recién definido</p><p>•     El flujo de trabajo está definido y aprobado por la ARB</p><p>•     Las implementaciones iniciales están en marcha.</p>                                                                                                                                                                                                                                                                                                |
| ------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p> </p><p>Descripción</p>                                                     | Este flujo de trabajo permite que un PoS solicite el estado de procesamiento actual de un reclamo en el FIS.                                                                                                                                                                                                                                                                                                                                          |
| <p> </p><p> </p><p>Ejemplo</p>                                                 | Un hospital ha enviado una reclamación de reembolso electrónico a la compañía de seguros. Después de un período de espera, el hospital quiere verificar si se tramitó la reclamación.                                                                                                                                                                                                                                                                 |
| Estado                                                                         | OHIE NIVEL 0                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| <p> </p><p>Estándares referenciados</p>                                        | Módulo de finanzas HL7 FHIR: [http://hl7.org/fhir/financial-module.html](http://hl7.org/fhir/financial-module.html)                                                                                                                                                                                                                                                                                                                                   |
| <p> </p><p> </p><p> </p><p>Supuestos y prerrequisitos</p>                      | <p> </p><p>•     El FIS administra el identificador único de reclamación</p><p> </p><p>•     El sistema de PoS ya envió una reclamación al FIS y recibió un identificador único para el reclamo (-> HFW-004)</p>                                                                                                                                                                                                                                      |
| <p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>Actores</p> | <p> </p><p>•     PoS: el sistema de punto de servicio que ha formulado una reclamación espera respuesta del FIS.</p><p>•     IOL: media en las transacciones entre el sistema PoS y los servicios de infraestructura para facilitar la interoperabilidad.</p><p>•     FIS: sistema de financiamiento y seguros que maneja el procesamiento de reclamaciones y el análisis de los siniestros.</p><p>•     EXT: una capa de pago externa (OpenHIE).</p> |
| <p> </p><p>Validaciones</p>                                                    | La IOL o el PoS debe validar los recursos que se envían de FHIR.                                                                                                                                                                                                                                                                                                                                                                                      |

### **Descripción de la interacción**

![](https://lh3.googleusercontent.com/d\_Dimas1cGGVCAObR51Eb3GhC0U\_PB0C9Eb\_ZwmBjUSrGXYMuTWfkvh3oomhZaAr7TWfuL463y1eOwO9-lW9AWSSovvdLg1onIe\_cU9fHyi9MXfXDcSHo0lQlcK\_s54TIfF2YaTW)

Código del recurso

(enlace al texto permanente en [https://www.websequencediagrams.com/](https://www.websequencediagrams.com))

```
title HFW-005: Claim Tracking
participant PoS
participant IOL
participant FIS

note over PoS, FIS
Assumes that claiming was done already (HFW-004: Claiming)

end note

PoS -> IOL: [1] Submit claim response query (Claim ID)
IOL -> FIS: [2] Forward query
FIS -> FIS: [3] Process query

alt accepted
	FIS -> IOL: [4] Return positive claim result
	IOL -> PoS: [5] Forward positive claim result
else rejected
	FIS -> IOL: [6] Return negative claim result
	IOL -> PoS: [7] Forward negative claim result
else queued
	FIS -> IOL: [8] Return queued status notification
	IOL -> PoS: [9] Forward queued status notification
else not found
	FIS -> IOL: [10] Return not found notification
	IOL -> PoS: [11] Forward not found notification
end
```

### **Detalles técnicos**



| Ref                      | Interacción                                                                                | Punto final                                                         | Datos                                                        | Especificaciones de la transacción                                                                  |
| ------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| <p> </p><p> </p><p>1</p> | <p> </p><p>Enviar la consulta de la respuesta de la reclamación (ID de la reclamación)</p> | <p> </p><p> </p><p>IOL</p>                                          | <p> </p><p>FHIR</p><p>positivo de la reclamación</p>         | <p> </p><p><a href="http://hl7.org/fhir/">http://hl7.org/fhir/</a> R4/claimrespons e.html</p>       |
| 2                        | Reenviar consulta                                                                          | FIS                                                                 |                                                              |                                                                                                     |
| 3                        | Proceso de consulta                                                                        | interno                                                             |                                                              |                                                                                                     |
| <p> </p><p> </p><p>4</p> | <p> </p><p>Devolver una respuesta sobre el resultado</p>                                   | <p> </p><p> </p><p>IOL</p>                                          | <p> </p><p>FHIR</p><p>positivo de la reclamación</p>         | <p> </p><p> </p><p><a href="http://hl7.org/fhir">http://hl7.org/fhir</a> R4/claimrespons e.html</p> |
| <p> </p><p>5</p>         | Reenviar el resultado positivo sobre la reclamación                                        | <p> </p><p>PoS</p>                                                  |                                                              |                                                                                                     |
| <p> </p><p> </p><p>6</p> | <p> </p><p> </p><p>Devolver el resultado negativo sobre la reclamación</p>                 | <p> </p><p> </p><p>IOL</p>                                          | <p> </p><p> </p><p>FHIR</p><p>positivo de la reclamación</p> | <p> </p><p> </p><p><a href="http://hl7.org/fhir">http://hl7.org/fhir</a> R4/claimrespons e.html</p> |
| <p> </p><p>7</p>         | Reenviar el resultado negativo sobre la reclamación                                        | <p> </p><p>PoS</p>                                                  |                                                              |                                                                                                     |
| <p> </p><p> </p><p>8</p> | <p> </p><p> </p><p>Devolver notificación de estado en cola</p>                             | <p> </p><p> </p><p>IOL</p>                                          | <p> </p><p> </p><p>FHIR</p><p>positivo de la reclamación</p> | <p> </p><p> </p><p><a href="http://hl7.org/fhir">http://hl7.org/fhir</a> R4/claimrespons e.html</p> |
| <p> </p><p>9</p>         | Reenviar notificación de estado en cola                                                    | <p> </p><p>PoS</p>                                                  |                                                              |                                                                                                     |
| 10                       | Notificación de devolución no encontrada                                                   | <p><strong>IOL</strong></p><p><strong>HTTP 404</strong></p><p> </p> |                                                              | https://[www.w3.org/](http://www.w3.org/) Protocols/rfc2616/ rfc2616-sec10.html                     |
| 11                       | Reenviar notificación de no encontrada                                                     | **PoS**                                                             |                                                              |                                                                                                     |
