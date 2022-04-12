# HFW-004: Claiming

| Workflow Maturity           | <p></p><p><img src="https://lh6.googleusercontent.com/Kxkqfa92YGW3mIOmWio0Twi4YLMA92z6mL1MuFzkx4AWS5CX5zbzWid5z4p2W-e6O66llKpaU0r6lzwyXfhbIiWmkVEuPDy6stX5x5L8uC2DkEXs6qUFX-7xxXTlb9hbkg" alt=""><br>Newly Defined </p><ul><li>Workflow is defined and ARB approved</li><li>Initial implementations are underway</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Description                 | <p>In the claiming process offers three functions </p><ol><li>Pre-determination: A PoS system (e.g. Hospital) requests an estimation of the expected reimbursement for a beneficiary’s specific treatment from the FIS (e.g Insurance). </li><li>Pre-authorization: A PoS system (e.g. Hospital) requests an approval for a specific treatment from the FIS (e.g Insurance). At the FIS a manual intervention is needed to authorize the requested treatment. The insurer might need to reserve funds in the budget.</li><li>Claiming: a PoS system (e.g. Hospital) sends a request for reimbursement of costs incurred for a certain treatment to the FIS</li></ol>                                                                                                                            |
| Example                     | <ol><li>An expensive treatment is needed and the Hospital wants to estimate the inputs they can apply. </li><li>A costly surgery is needed and has to be pre-approved by the insurance before it can be done. </li><li>A patient was treated in the hospital and the hospital requests reimbursement of the incurred costs.</li></ol>                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Status                      | OHIE LEVEL 1 - Emerging Collection                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Referenced Standards        | <ul><li>HL7 FHIR Financial Module: <a href="http://hl7.org/fhir/financial-module.html">http://hl7.org/fhir/financial-module.html</a></li><li>Treatment plan submitted to Insurer to reserve funds: <a href="http://hl7.org/fhir/claim.html">Claim</a> {use=preauthorization} (<a href="http://hl7.org/fhir/financial-module.html#order">http://hl7.org/fhir/financial-module.html#order</a>)</li></ul>                                                                                                                                                                                                                                                                                                                                                                                          |
| Assumptions & Prerequisites | <ul><li>The PoS system has a curated list of insurance providers that interact with that system </li><li>All relevant patient data is available in the PoS.</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Actors                      | <ul><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/point-of-care-systems">PoS</a> - The point of service system that captures a patient clinical encounter and sends the formatted claim to the HIE. </li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/openhie-interoperability-layer-iol">IOL</a> - Mediates the transactions between the PoS system and the infrastructure services to facilitate easier interoperability. </li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/openhie-finance-and-insurance-service">FIS</a> - Financing and Insurance System that manages the claims processing and scrutinisation. </li><li>EXT - an (OpenHIE) external payment layer</li></ul> |
| Validations                 | The PoS or IOL should validate the FHIR resources being submitted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

### Interaction Description

![](https://lh3.googleusercontent.com/1hcKyIWDVT39Q71qOsZWmx\_NyGPh7n3IIBiO\_TxjZ0W9Reu20ouS50xgTxnCguizWjPQFCcQZ36dxR3DSJCEHdcUP8mOmLHEsLxnxoFLyEgQFp5Bd-z0MTYWb\_aeWMQjcVj018Cq)

**Source code**

&#x20;(link to permanent text in [https://www.websequencediagrams.com/](https://www.websequencediagrams.com))

```
title HFW-004: Claiming
participant PoS
participant IOL
participant FIS
participant EXT


opt Get code lists for medical procedures & items
	PoS -> IOL: [1] Submit medical procedures & items query
	IOL -> FIS: [2] Forward query
	FIS -> FIS: [3] Process query
	FIS -> IOL: [4] Return  medical procedures & items
	IOL -> PoS: [5] Forward medical procedures & items
end opt
 

PoS -> PoS: [6] Build claim
PoS -> IOL: [7] Submit claim (use)
IOL -> FIS: [8] Forward query
FIS -> FIS: [9] Process claim

alt accepted
	opt Payout
    	note over IOL, EXT: [10] Process payment
	end opt
	FIS -> IOL: [11] Return positive claim result
	IOL -> PoS: [12] Forward positive claim result
else rejected
	FIS -> IOL: [13] Return negative claim result
	IOL -> PoS: [14] Forward negative claim result
else queued
	FIS -> IOL: [15] Return queued status notification
	IOL -> PoS: [16] Forward queued status notification
end
```

### Technical Details

| Ref | Interaction                             | Endpoint | Data                                                                    | Transaction Spec                                                                                                                                                                                    |
| --- | --------------------------------------- | -------- | ----------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Submit medical procedures & items query | IOL      | FHIR ActivityDefinition, FHIR Medication                                | <p><a href="http://hl7.org/fhir/R4/activitydefinition.htmlhttp://hl7.org/fhir/R4/medication.html">http://hl7.org/fhir/R4/activitydefinition.html<br>http://hl7.org/fhir/R4/medication.html </a></p> |
| 2   | Forward query                           | FIS      |                                                                         |                                                                                                                                                                                                     |
| 3   | Process query                           | internal |                                                                         |                                                                                                                                                                                                     |
| 4   | Return  medical procedures & items      | IOL      | FHIR ActivityDefinition, FHIR Medication                                | <p><a href="http://hl7.org/fhir/R4/activitydefinition.htmlhttp://hl7.org/fhir/R4/medication.html">http://hl7.org/fhir/R4/activitydefinition.html<br>http://hl7.org/fhir/R4/medication.html </a></p> |
| 5   | Forward medical procedures & items      | PoS      |                                                                         |                                                                                                                                                                                                     |
| 6   | Build claim                             | internal |                                                                         |                                                                                                                                                                                                     |
| 7   | Submit claim (use)                      | IOL      | FHIR Claim (use=\[preauthorizsation, predetermination , claim])         | [http://hl7.org/fhir/R4/claim.html ](http://hl7.org/fhir/R4/claim.html)                                                                                                                             |
| 8   | Forward query                           | FIS      |                                                                         |                                                                                                                                                                                                     |
| 9   | Process claim                           | internal |                                                                         |                                                                                                                                                                                                     |
| 10  | Process payment                         | EXT      |                                                                         |                                                                                                                                                                                                     |
| 11  | Return positive claim result            | IOL      | FHIR ClaimResponse                                                      | [http://hl7.org/fhir/R4/claimresponse.html ](http://hl7.org/fhir/R4/claimresponse.html)                                                                                                             |
| 12  | Forward positive claim result           | PoS      |                                                                         |                                                                                                                                                                                                     |
| 13  | Return negative claim result            | IOL      | FHIR ClaimResponse (use=\[preauthorizsation, predetermination , claim]) | [http://hl7.org/fhir/R4/claimresponse.html ](http://hl7.org/fhir/R4/claimresponse.html)                                                                                                             |
| 14  | Forward negative claim result           | PoS      |                                                                         |                                                                                                                                                                                                     |
| 15  | Return queued status notification       | IOL      | FHIR ClaimResponse (use=\[preauthorizsation, predetermination , claim]) | [http://hl7.org/fhir/R4/claimresponse.html ](http://hl7.org/fhir/R4/claimresponse.html)                                                                                                             |
| 16  | Forward queued status notification      | PoS      |                                                                         |                                                                                                                                                                                                     |

