# HFW-001: Enroll Beneficiary

This transaction allows a POS system to enroll a patient/beneficiary into a Health Financing and Insurance System, to save patient/beneficiary level demographic data to a Client Registry (optional) and to save the beneficiary insurance identifier to a Client Registry (optional). Coverage eligibility can be verified beforehand.

Example Use Cases&#x20;

* A field agent of the national insurance provider registers a household into a specific insurance scheme.

| Workflow Maturity           | <p><img src="https://lh6.googleusercontent.com/Kxkqfa92YGW3mIOmWio0Twi4YLMA92z6mL1MuFzkx4AWS5CX5zbzWid5z4p2W-e6O66llKpaU0r6lzwyXfhbIiWmkVEuPDy6stX5x5L8uC2DkEXs6qUFX-7xxXTlb9hbkg" alt=""><br>Newly Defined </p><ul><li>Workflow is defined and ARB approved</li><li>Initial implementations are underway</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Referenced Standards        | HL7 FHIR Financial Module: [http://hl7.org/fhir/financial-module.html](http://hl7.org/fhir/financial-module.html)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Assumptions & Prerequisites | <ul><li>The registration process uses existing Patient Identity Management processes for registration and querying</li><li>Unique insuree identifier is managed by FIS</li><li>IOL implicitly verifies all messages for syntax</li><li>The PoS system has a curated list of FIS that interact with that system</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Actors                      | <ul><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/point-of-care-systems">PoS</a> - The point of service system that captures an enrollment request.</li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/openhie-interoperability-layer-iol">IOL</a> - Mediates the transactions between the PoS system and the infrastructure services to facilitate easier interoperability.</li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/client-registry">CR</a> - The source of truth for patient demographic and identifier detail. It is able to be queried using an identifier to find the enterprise identifier for a particular person.</li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/openhie-finance-and-insurance-service">FIS</a> - Financing and Insurance System that manages data on beneficiaries and their coverage.</li></ul> |
| Validations                 | The IOL should validate the FHIR resources being submitted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

### Interaction Description

![](https://lh6.googleusercontent.com/fmajevYyrLOg-YJWI1vo1Hn7pHPIlom2LF1XUT30k81oRIEGaMie2MgtCslYA-K5EABKWrqq4Xo7fxy8Ke-ibowp63Ti9YD-ZlC62l5CIpoCRcJR03yHxoL-AP1-uXSogNTYbQ8M)

#### Source code&#x20;

(link to permanent text in [https://www.websequencediagrams.com/](https://www.websequencediagrams.com))&#x20;

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

### Technical Details

| #  | Interaction                          | Endpoint | Data                                              | Transaction Options                                                                                                                         |
| -- | ------------------------------------ | -------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| 1  | Fetch / Register patient             | CR       |                                                   | (CRWF-1,3,4)                                                                                                                                |
| 2  | Submit enrollment request            | IOL      |                                                   |                                                                                                                                             |
| 3  | Forward enrollment request           | FIS      | FHIR Contract(Patient,Organization,InsurancePlan) | http://hl7.org/fhir/contract.html                                                                                                           |
| 4  | Verify enrollment eligibility        | internal |                                                   |                                                                                                                                             |
| 5  | Process enrollment                   | internal |                                                   |                                                                                                                                             |
| 6  | Register HF identifier with CR       | CR       |                                                   | [(CRWF-2)](https://guides.ohie.org/arch-spec/introduction/patient-identity-management-workflows/update-patient-demographic-record-workflow) |
| 7  | Return positive enrollment response  | IOL      | FHIR Contract(Patient,Organization,InsurancePlan) | http://hl7.org/fhir/contract.html                                                                                                           |
| 8  | Forward positive enrollment response | POS      |                                                   |                                                                                                                                             |
| 9  | Add details to patient record        | internal |                                                   |                                                                                                                                             |
| 10 | Return negative enrollment           | IOL      | FHIR Contract(Patient,Organization,InsurancePlan) | http://hl7.org/fhir/contract.html                                                                                                           |
| 11 | Forward negative enrollment response | POS      |                                                   |                                                                                                                                             |
