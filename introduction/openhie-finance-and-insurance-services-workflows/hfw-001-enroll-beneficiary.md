# HFW-001: Inscribir beneficiarios

Esta transacción permite que un sistema de PoS inscriba a un paciente/beneficiario en un sistema de servicios financieros y de seguros de salud, guarde los datos demográficos del paciente/beneficiario o el identificador del seguro en un registro de clientes (opcional). La elegibilidad de la cobertura se puede verificar de antemano.

Ejemplos de casos de uso

•    Un agente de campo del proveedor de seguros nacional registra un hogar en un plan de seguro específico.



| <p> </p><p>Madurez del flujo de trabajo</p>                                            | <p><img src="file:///Users/dtrefun/Library/Group%20Containers/UBF8T346G9.Office/TemporaryItems/msohtmlclip/clip_image001.jpg" alt=""></p><p>Recién definido</p><p>·       El flujo de trabajo está definido y aprobado por la ARB.</p><p>·       Las implementaciones iniciales están en marcha.</p>                                                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p> </p><p>Estándares referenciados</p>                                                | Módulo de finanzas HL7 FHIR: [http://hl7.org/fhir/financial-module.html](http://hl7.org/fhir/financial-module.html)                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| <p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>Supuestos y prerrequisitos</p>      | <p> </p><p>•     El proceso de registro utiliza los procesos existentes de gestión de identidad del paciente para el registro y la consulta.</p><p>•     El Servicio de Finanzas y Seguros (Finance and Insurance Service, FIS) gestiona el identificador único del asegurado.</p><p> </p><p>•     IOL verifica implícitamente todos los mensajes para la sintaxis</p><p>•     El sistema de PoS tiene una lista seleccionada del FIS que interactúa con ese sistema</p>                                                                                                                        |
| <p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p> </p><p>Actores</p> | <p> </p><p>•     PoS: el sistema de punto de servicio que captura la solicitud de inscripción.</p><p>•     IOL: media las transacciones entre el sistema PoS y los servicios de infraestructura para facilitar la interoperabilidad.</p><p>•     CR: la fuente de la verdad para la demografía del paciente y los detalles del identificador. Se puede consultar utilizando un identificador para encontrar el identificador de la empresa para una persona en particular.</p><p>•     FIS: sistema de financiamiento y seguros que maneja los datos de los beneficiarios y sus coberturas.</p> |

### **Descripción de la interacción**

![](https://lh6.googleusercontent.com/fmajevYyrLOg-YJWI1vo1Hn7pHPIlom2LF1XUT30k81oRIEGaMie2MgtCslYA-K5EABKWrqq4Xo7fxy8Ke-ibowp63Ti9YD-ZlC62l5CIpoCRcJR03yHxoL-AP1-uXSogNTYbQ8M)

**Código del recurso**

(enlace hacia el texto permanente en https://[www.websequencediagrams.com/)](http://www.websequencediagrams.com/\))

```
title HFW-001: Enroll beneficiary
participant PoS
participant IOL
participant FIS
participant CR

note over PoS, CR
Assumes that registration or querying of CR is done here

PoS->HIE: [1] Fetch / Register patient (CRWF-1,3,4)
end Note

PoS->IOL: [2] Submit enrollment request
IOL->FIS: [3] Forward enrollment request
FIS->FIS: [4] Verify enrollment eligibility

alt success
  FIS->FIS: [5] Process enrollment
  opt
	FIS->CR: [6] * Register HF identifier with CR (CRWF-2)
  end
  FIS->IOL: [7] Return positive enrollment response
  IOL->PoS: [8] Forward positive enrollment response
  PoS->PoS: [9] Add details to patient record
else validation error
  FIS->IOL: [10] Return negative enrollment response
  IOL->PoS: [11] Forward negative enrollment response
end

```

### **Detalles técnicos**



| <p> <strong></strong> </p><p>N.º</p>                          | <p> <strong></strong> </p><p>Interacción</p>                                                 | <p> <strong></strong> </p><p>Punto final</p>                   | <p> <strong></strong> </p><p>Datos</p>                               | Opciones de transacciones                                                                              |
| ------------------------------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| <p> <strong></strong> </p><p>1</p>                            | Recuperar/registrar la información del paciente                                              | <p> <strong></strong> </p><p>CR</p>                            |                                                                      | <p> <strong></strong> </p><p>(CRWF-1,3,4)</p>                                                          |
| <p> <strong></strong> </p><p>2</p>                            | Enviar la solicitud de inscripción                                                           | <p> <strong></strong> </p><p>IOL</p>                           |                                                                      |                                                                                                        |
| <p> <strong></strong> </p><p> <strong></strong> </p><p>3</p>  | <p> <strong></strong> </p><p>Reenviar solicitud de inscripción</p>                           | <p> <strong></strong> </p><p> <strong></strong> </p><p>FIS</p> | <p>FHIR</p><p>Contracto (paciente, organización, plan de seguro)</p> | <p> <strong></strong> </p><p><a href="http://hl7.org/fhir/">http://hl7.org/fhir/</a> contract.html</p> |
| <p> <strong></strong> </p><p>4</p>                            | Verificación de la elegibilidad para inscripción                                             | <p> <strong></strong> </p><p>interno</p>                       |                                                                      |                                                                                                        |
| <p> <strong></strong> </p><p>5</p>                            | Proceso de inscripción                                                                       | <p> <strong></strong> </p><p>interno</p>                       |                                                                      |                                                                                                        |
| <p> <strong></strong> </p><p>6</p>                            | Registrar el identificador HF con el CR                                                      | <p> <strong></strong> </p><p>CR</p>                            |                                                                      | <p> <strong></strong> </p><p>(CRWF-2)</p>                                                              |
| <p> <strong></strong> </p><p> <strong></strong> </p><p>7</p>  | <p> <strong></strong> </p><p>Devolver una respuesta de inscripción positiva</p>              | <p> <strong></strong> </p><p> <strong></strong> </p><p>IOL</p> | <p>FHIR</p><p>Contracto (paciente, organización, plan de seguro)</p> | <p> <strong></strong> </p><p><a href="http://hl7.org/fhir">http://hl7.org/fhir</a> ontract.html</p>    |
| <p> <strong></strong> </p><p> <strong></strong> </p><p>8</p>  | Reenviar una respuesta de inscripción positiva                                               | <p> <strong></strong> </p><p> <strong></strong> </p><p>POS</p> |                                                                      |                                                                                                        |
| <p> <strong></strong> </p><p>9</p>                            | Agregar detalles del registro del paciente                                                   | <p> <strong></strong> </p><p>interno</p>                       |                                                                      |                                                                                                        |
| <p> <strong></strong> </p><p> <strong></strong> </p><p>10</p> | <p> <strong></strong> </p><p> <strong></strong> </p><p>Devolver una inscripción negativa</p> | <p> <strong></strong> </p><p> <strong></strong> </p><p>IOL</p> | <p>FHIR</p><p>Contracto (paciente, organización, plan de seguro)</p> | <p> <strong></strong> </p><p><a href="http://hl7.org/fhir/">http://hl7.org/fhir/</a> ontract.html</p>  |
