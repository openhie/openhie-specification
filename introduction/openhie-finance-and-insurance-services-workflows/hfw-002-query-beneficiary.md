# HFW-002: Query Beneficiary

The PoS system is searching for beneficiary master data in the FIS based on a specific query (e.g. by name, ID, age etc …). The FIS returns all master data from the CR and adds FIS specific master data .

Example use case: An insurance agent is looking for information about a beneficiary to respond to a service desk call.

| Workflow Maturity           | <p></p><p><img src="https://lh6.googleusercontent.com/Kxkqfa92YGW3mIOmWio0Twi4YLMA92z6mL1MuFzkx4AWS5CX5zbzWid5z4p2W-e6O66llKpaU0r6lzwyXfhbIiWmkVEuPDy6stX5x5L8uC2DkEXs6qUFX-7xxXTlb9hbkg" alt=""><br>Newly Defined </p><ul><li>Workflow is defined and ARB approved</li><li>Initial implementations are underway</li></ul>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| --------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Standards                   | HL7 FHIR Financial Module: [http://hl7.org/fhir/financial-module.html](http://hl7.org/fhir/financial-module.html)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Assumptions & Prerequisites | None                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| Actors                      | <ul><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/point-of-care-systems">PoS</a> - The point of service system that captures a patient clinical encounter, it is responsible for sending this encounter on to the HIE. </li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/openhie-interoperability-layer-iol">IOL</a> - Mediates the transactions between the PoS system and the infrastructure services to facilitate easier interoperability. </li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/client-registry">CR</a> - The source of truth for patient demographic and identifier detail. It is able to be queried using an identifier to find the enterprise identifier for a particular person. </li><li><a href="https://guides.ohie.org/arch-spec/openhie-component-specifications-1/openhie-finance-and-insurance-service">FIS</a> - Financing and Insurance System that manages data on beneficiaries and their coverage.</li></ul> |
| Validations                 | The IOL should validate the FHIR resources being submitted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

### Interaction Description

![](https://lh4.googleusercontent.com/8UtCFR0lYK-95WiyXkVKIqimDPONMb\_SWcPXQ5Sly6E7CVc2qaMwBlh8VPXwLr8MZsRnAJkkIkCgjZkOS37AvR61pI2Puk70pGX808kW4ulKbdOgxwa7nPAemZvdHljdbgUb1-m9)

#### Source Code

&#x20;(link to permanent text in [https://www.websequencediagrams.com/](https://www.websequencediagrams.com))

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

### Technical Details

| Ref | Interaction                          | Endpoint | Data         | Transaction Spec                                                     |
| --- | ------------------------------------ | -------- | ------------ | -------------------------------------------------------------------- |
| 1   | Fetch / Register patient             | CR       |              | (CRWF-1,3,4)                                                         |
| 2   | Submit Patient/Beneficiary Query     | IOL      |              |                                                                      |
| 3   | Forward Query details                | FIS      | FHIR Patient | [http://hl7.org/fhir/patient.html](http://hl7.org/fhir/patient.html) |
| 4   | Process query                        | internal |              |                                                                      |
| 5   | Return Beneficiary Details response  | IOL      | FHIR Patient | [http://hl7.org/fhir/patient.html](http://hl7.org/fhir/patient.html) |
| 6   | Forward Beneficiary Details response | POS      |              |                                                                      |

