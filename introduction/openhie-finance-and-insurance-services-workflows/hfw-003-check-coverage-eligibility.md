# HFW-003: Check Coverage Eligibility

This workflow can be used to check if a patient is enrolled in coverage and optionally examining whether specific services can be applied.

Example use cases:

* If a mother presents at a hospital, this workflow can be used to determine if she is enrolled in the MCH postnatal care scheme of the MoH.
* A patient is diagnosed with cancer and needs chemotherapy. The hospital inquires about coverage for chemotherapy.

| Workflow Maturity           | <p><img src="https://lh6.googleusercontent.com/Kxkqfa92YGW3mIOmWio0Twi4YLMA92z6mL1MuFzkx4AWS5CX5zbzWid5z4p2W-e6O66llKpaU0r6lzwyXfhbIiWmkVEuPDy6stX5x5L8uC2DkEXs6qUFX-7xxXTlb9hbkg" alt=""><br>Newly Defined</p><ul><li>Workflow is defined and ARB approved</li><li>Initial implementations are underway</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Standards                   | <ul><li>HL7 FHIR Financial Module: <a href="http://hl7.org/fhir/financial-module.html">http://hl7.org/fhir/financial-module.html</a></li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Assumptions & Prerequisites | None                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Actors                      | <ul><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/point-of-care-systems">PoS</a> - The point of service system that captures a patient clinical encounter, it is responsible for sending this encounter on to the HIE.</li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/openhie-interoperability-layer-iol">IOL</a> - Mediates the transactions between the PoS system and the infrastructure services to facilitate easier interoperability.</li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/client-registry">CR</a> - The source of truth for patient demographic and identifier detail. It is able to be queried using an identifier to find the enterprise identifier for a particular person.</li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/openhie-finance-and-insurance-service">FIS</a> - Financing and Insurance System that manages data on beneficiaries and their coverage.</li></ul> |
| Validations                 | The PoS or IOL should validate the FHIR resources being submitted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

### Interaction Description

![](https://lh6.googleusercontent.com/nGHZHLc5wa6NUe9utNSFkDWHIl2zaAq88pA-E1anht-t5lIiiZt-aF\_uOfuyYktkd4N2BvAs6Hkcv\_tHVA50L\_0HtSFIfwL8Y09bbodxBCrqdov66xPX\_s4DREqOsGVI8Wbhb9-0)

#### Source Code

(link to permanent text in [https://www.websequencediagrams.com/](https://www.websequencediagrams.com))

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

### Technical Details

| Ref | Interaction                             | Endpoint | Data                                     | Transaction Spec                                                                                                                                                                                   |
| --- | --------------------------------------- | -------- | ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Submit Medical Procedures & Items Query | IOL      |                                          |                                                                                                                                                                                                    |
| 2   | Forward Query                           | FIS      | FHIR ActivityDefinition, FHIR Medication | <p><a href="http://hl7.org/fhir/R4/activitydefinition.htmlhttp://hl7.org/fhir/R4/medication.html">http://hl7.org/fhir/R4/activitydefinition.html<br>http://hl7.org/fhir/R4/medication.html</a></p> |
| 3   | Process query                           | internal |                                          |                                                                                                                                                                                                    |
| 4   | Return Medical Procedures & Items       | IOL      | FHIR ActivityDefinition, FHIR Medication | <p><a href="http://hl7.org/fhir/R4/activitydefinition.htmlhttp://hl7.org/fhir/R4/medication.html">http://hl7.org/fhir/R4/activitydefinition.html<br>http://hl7.org/fhir/R4/medication.html</a></p> |
| 5   | Forward Medical Procedures & Items      | POS      |                                          |                                                                                                                                                                                                    |
| 6   | Submit Coverage Eligibility Query       | IOL      |                                          |                                                                                                                                                                                                    |
| 7   | Forward Query                           | FIS      | FHIR CoverageEligibilityRequest          | [http://hl7.org/fhir/R4/coverageeligibilityrequest.html](http://hl7.org/fhir/R4/coverageeligibilityrequest.html)                                                                                   |
| 8   | Process Insuree Query                   | internal |                                          |                                                                                                                                                                                                    |
| 9   | Process Policy Query                    | internal |                                          |                                                                                                                                                                                                    |
| 10  | Return Coverage Eligibility Result      | IOL      | FHIR CoverageEligibilityResponse         | [http://hl7.org/fhir/R4/coverageeligibilityresponse.html](http://hl7.org/fhir/R4/coverageeligibilityresponse.html)                                                                                 |
| 11  | Forward Coverage Eligibility Result     | POS      |                                          |                                                                                                                                                                                                    |
