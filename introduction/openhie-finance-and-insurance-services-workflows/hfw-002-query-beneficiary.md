# HFW-002: Consulta del beneficiario

El sistema de PoS está buscando datos maestros de beneficiarios en el FIS con base en una consulta específica (p. ej., por nombre, ID, edad, etc.). El FIS devuelve todos los datos maestros del CR y agrega datos maestros específicos de FIS.

Ejemplo de caso de uso: un agente de seguros está buscando información sobre un beneficiario para responder a una llamada de la mesa de servicio.



| Madurez del flujo de trabajo                                                           | <p><img src="file:///Users/dtrefun/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image001.jpg" alt=""></p><p>Recién definido</p><p>·       El flujo de trabajo está definido y aprobado por la ARB.</p><p>·       Las implementaciones iniciales están en marcha.</p>                                                                                                                                                                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p> </p><p>Estándares</p>                                                              | Módulo de finanzas HL7 FHIR: [http://hl7.org/fhir/financial-module.html](http://hl7.org/fhir/financial-module.html)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Supuestos y prerrequisitos                                                             | Ninguno                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| <p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>Actores</p> | <p> </p><p>•     PoS: el sistema de punto de servicio que captura un encuentro clínico con un paciente es responsable de enviar este encuentro al HIE.</p><p>•     IOL: media en las transacciones entre el sistema PoS y los servicios de infraestructura para facilitar la interoperabilidad.</p><p>•     CR: la fuente de la verdad para los detalles demográficos e identificadores del paciente. Se puede consultar utilizando un identificador para encontrar el identificador de la empresa para una persona en particular.</p><p>•     FIS: sistema de financiamiento y seguros que maneja los datos de los beneficiarios y sus coberturas.</p> |
| <p> </p><p>Validaciones</p>                                                            | La IOL debe validar los recursos que se envían de FHIR.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

### **Descripción de la interacción**

![](https://lh4.googleusercontent.com/8UtCFR0lYK-95WiyXkVKIqimDPONMb\_SWcPXQ5Sly6E7CVc2qaMwBlh8VPXwLr8MZsRnAJkkIkCgjZkOS37AvR61pI2Puk70pGX808kW4ulKbdOgxwa7nPAemZvdHljdbgUb1-m9)

**Código del recurso**

(enlace hacia el texto permanente en [https://www.websequencediagrams.com/](https://www.websequencediagrams.com))

```
title HFW-002: Query Beneficiary

participant PoS
participant IOL
participant FIS
participant CR

opt
  note over PoS, CR
	Assumes that querying of CR is done here
    
	PoS->HIE: [1] Fetch patient (CRWF-3,4)
  end Note
end opt
PoS->IOL: [2] Submit Patient/Beneficiary Query (Demographics / ID)
IOL->FIS: [3] Forward Query details

FIS->FIS: [4] Process query

FIS->IOL: [5] Return Beneficiary Details response

IOL->PoS: [6] Forward Beneficiary Details response
```

### **Detalles técnicos**



| Ref                                                                           | Interacción                                                 | Punto final                                                    | Datos                           | Especificaciones de la transacción                                                |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------- | -------------------------------------------------------------- | ------------------------------- | --------------------------------------------------------------------------------- |
| <p> <strong></strong> </p><p>1</p>                                            | Recuperar/registrar la información del paciente             | <p> <strong></strong> </p><p>CR</p>                            |                                 | <p> <strong></strong> </p><p>(CRWF-1,3,4)</p>                                     |
| <p> <strong></strong> </p><p> <strong></strong> </p><p>2</p>                  | Enviar consulta de la información del paciente/beneficiario | <p> <strong></strong> </p><p> <strong></strong> </p><p>IOL</p> |                                 |                                                                                   |
| <p> <strong></strong> </p><p><strong>3</strong></p>                           | Reenviar detalles de la consulta.                           | <p> <strong></strong> </p><p><strong>FIS</strong></p>          | <p> </p><p>Paciente de FHIR</p> | <p> </p><p><a href="http://hl7.org/fhir">http://hl7.org/fhir</a> patient.html</p> |
| **4**                                                                         | Proceso de consulta                                         | **interno**                                                    |                                 |                                                                                   |
| <p> <strong></strong> </p><p> <strong></strong> </p><p><strong>5</strong></p> | Devolver respuesta de detalles del beneficiario             | <p> <strong></strong> </p><p><strong>IOL</strong></p>          | <p> </p><p>Paciente de FHIR</p> | <p> </p><p><a href="http://hl7.org/fhir">http://hl7.org/fhir</a> patient.html</p> |
| <p> <strong></strong> </p><p><strong>6</strong></p>                           | Reenviar respuesta de detalles del beneficiario             | <p> <strong></strong> </p><p><strong>POS</strong></p>          |                                 |                                                                                   |
