# HFW-005: Claim Tracking

| Workflow Maturity           | <p></p><p></p><p><img src="https://lh6.googleusercontent.com/Kxkqfa92YGW3mIOmWio0Twi4YLMA92z6mL1MuFzkx4AWS5CX5zbzWid5z4p2W-e6O66llKpaU0r6lzwyXfhbIiWmkVEuPDy6stX5x5L8uC2DkEXs6qUFX-7xxXTlb9hbkg" alt=""><br>Newly Defined </p><ul><li>Workflow is defined and ARB approved</li><li>Initial implementations are underway</li></ul>                                                                                     |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Description                 | This workflow allows a PoS to request the current processing status of a claim in the FIS.                                                                                                                                                                                                                                                                                                                            |
| Example                     | A hospital has sent an electronic reimbursement claim to the insurance company. After a waiting period the hospital wants to verify if the claim was processed.                                                                                                                                                                                                                                                       |
| Status                      | OHIE LEVEL 0                                                                                                                                                                                                                                                                                                                                                                                                          |
| Referenced Standards        | HL7 FHIR Financial Module: [http://hl7.org/fhir/financial-module.html](http://hl7.org/fhir/financial-module.html)                                                                                                                                                                                                                                                                                                     |
| Assumptions & Prerequisites | <ul><li>Unique claim identifier is managed by FIS</li><li>The PoS system has already sent a claim to the FIS and has received a unique identifier for the claim (-> HFW-004)</li></ul>                                                                                                                                                                                                                                |
| Actors                      | <ul><li>PoS - The point of service system that has formulated a claim and waits for a response from the FIS. </li><li>IOL - Mediates the transactions between the PoS system and the infrastructure services to facilitate easier interoperability. </li><li>FIS - Financing and Insurance System that manages the claims processing and scrutinisation. </li><li>EXT - an (OpenHIE) external payment layer</li></ul> |
| Validations                 | The PoS or IOL should validate the FHIR resources being submitted.                                                                                                                                                                                                                                                                                                                                                    |



### Interaction Description

![](https://lh3.googleusercontent.com/d\_Dimas1cGGVCAObR51Eb3GhC0U\_PB0C9Eb\_ZwmBjUSrGXYMuTWfkvh3oomhZaAr7TWfuL463y1eOwO9-lW9AWSSovvdLg1onIe\_cU9fHyi9MXfXDcSHo0lQlcK\_s54TIfF2YaTW)

#### Source Code

(link to permanent text in [https://www.websequencediagrams.com/](https://www.websequencediagrams.com))

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

### Technical Details

| Ref | Interaction                            | Endpoint | Data               | Transaction Spec                                                                                                    |
| --- | -------------------------------------- | -------- | ------------------ | ------------------------------------------------------------------------------------------------------------------- |
| 1   | Submit claim response query (Claim ID) | IOL      | FHIR ClaimResponse | [http://hl7.org/fhir/R4/claimresponse.html ](http://hl7.org/fhir/R4/claimresponse.html)                             |
| 2   | Forward query                          | FIS      |                    |                                                                                                                     |
| 3   | Process query                          | internal |                    |                                                                                                                     |
| 4   | Return positive claim result           | IOL      | FHIR ClaimResponse | [http://hl7.org/fhir/R4/claimresponse.html ](http://hl7.org/fhir/R4/claimresponse.html)                             |
| 5   | Forward positive claim result          | PoS      |                    |                                                                                                                     |
| 6   | Return negative claim result           | IOL      | FHIR ClaimResponse | [http://hl7.org/fhir/R4/claimresponse.html ](http://hl7.org/fhir/R4/claimresponse.html)                             |
| 7   | Forward negative claim result          | PoS      |                    |                                                                                                                     |
| 8   | Return queued status notification      | IOL      | FHIR ClaimResponse | [http://hl7.org/fhir/R4/claimresponse.html ](http://hl7.org/fhir/R4/claimresponse.html)                             |
| 9   | Forward queued status notification     | PoS      |                    |                                                                                                                     |
| 10  | Return not found notification          | IOL      | HTTP 404           | [https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html ](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) |
| 11  | Forward not found notification         | PoS      |                    |                                                                                                                     |
