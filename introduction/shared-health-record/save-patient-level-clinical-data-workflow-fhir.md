# Save Patient-level Clinical Data Workflow (FHIR native)

This transaction allows a point of service (PoS) system to save patient-level clinical data to the SHR. The transaction is verified and validated against necessary metadata before it is saved in the SHR. The following sequence diagram shows the steps involved.

| **Workflow Maturity**         | <p><img src="https://lh6.googleusercontent.com/Kxkqfa92YGW3mIOmWio0Twi4YLMA92z6mL1MuFzkx4AWS5CX5zbzWid5z4p2W-e6O66llKpaU0r6lzwyXfhbIiWmkVEuPDy6stX5x5L8uC2DkEXs6qUFX-7xxXTlb9hbkg" alt=""></p><p><strong>Newly Defined</strong></p> | <ul><li><strong>Workflow is newly defined</strong></li><li><strong>Initial implementations are being implemented</strong></li></ul>  |
| --- | --- | --- |
| Standards |  | HL7 FHIR |
| Assumptions and Prerequisites |  | <ul><li>The PoS system has a curated list of Providers that interact with that system, with knowledge of at least the providers that are relevant to that PoS system.</li><li>The PoS system has a curated list of Facilities that this system serves, with knowledge of at least one member (itself).</li><li>The PoS system is a trusted application known by the HIE and it is registered with the interoperability layer to be able to send and receive data securely (<a href="https://wiki.ohie.org/display/documents/Common+message+security+workflow">Common message security workflow</a>).</li> |
| Actors |  | <ul><li>PoS - The point of service system that captures a patient clinical encounter, it is responsible for sending this encounter on to the HIE.</li><li>IL - Mediates the transactions between the PoS system and the infrastructure services to facilitate easier interoperability.</li><li>CR - The source of truth for patient demographic and identifier detail. It is able to be queried to find the identities of a patient.</li><li>SHR - Stored patients clinical information. It is able to receive and store a patient clinical data.</li></ul> |

## **Interaction Description**

The following is a description of the interaction steps.

[![](https://mermaid.ink/img/pako:eNqNVE1v2kAQ_Ssjn4LkVqVJvzjkUEgVJBKQnfZS-7DxjmGE2XV310lQlP_eWRscYgjigICdN7Pvzbyd5yDTEoNBYPFfhSrDEYm5EatEAZTCOMqoFMrBTMfdo_F00j0aRt2T-DqCs1_X4whiNA9oeonyEC734fKSKwzgbz-FGvCzUrJAHxWZowfhcHsFf7XozyncGaFs4eMOzYqULvR8DV6H7aLPU7h6coYLwkw4QmYUodWVyfAVOowYeZHCbBrftbCGdK7NSrjeG1KNyGG0zfySwtCgjwhQ-AgGM21kCJQD52YLtOA04BNZR2oOze1AEkTF5wWpJWBhEUyl6n8Mai9oVHxNmbUvCuORD0nskGl07PWaU7-lMNF6WZVgXXXPo2nUmZ0mtLUOzAr2D1tW3z0rVxnVVtUGbn9PJh2KB8uKgg2Uw-20Ta4btDfAHyncaEn5Gu5re8BZ7AyV7ZhGuNLs13JBmQ1BSMkdYXU5PJJbvHbNT2CT8tH3OGSME6SYMs1JiaKN8lzOqopkr6ZZD4Z5HifZ_7THMsKyEDzmbsOB79xgaoZ7zWEfl-sNO2-Xt6y9QP6QI-1Jn6S1EaLkcaP0-5sHUAtB-e6bPNklB2_h5_tHFCR9pTpWGp1TgTy8ncccQi4yKsitQSi508QcjV9S9rgz--femrbUyuIpZmy6wjvJ5168m8uwIAxWTFOQ5JX57ONJ4Ba4wiQY8E8pzDIJEvXCuKr0Iq94VtoEg1ywk8LAP_l4rbJg4EyFW9Bm57YorJNumsVc7-eX_7nD3qM?type=png)](https://mermaid.live/edit#pako:eNqNVE1v2kAQ_Ssjn4LkVqVJvzjkUEgVJBKQnfZS-7DxjmGE2XV310lQlP_eWRscYgjigICdN7Pvzbyd5yDTEoNBYPFfhSrDEYm5EatEAZTCOMqoFMrBTMfdo_F00j0aRt2T-DqCs1_X4whiNA9oeonyEC734fKSKwzgbz-FGvCzUrJAHxWZowfhcHsFf7XozyncGaFs4eMOzYqULvR8DV6H7aLPU7h6coYLwkw4QmYUodWVyfAVOowYeZHCbBrftbCGdK7NSrjeG1KNyGG0zfySwtCgjwhQ-AgGM21kCJQD52YLtOA04BNZR2oOze1AEkTF5wWpJWBhEUyl6n8Mai9oVHxNmbUvCuORD0nskGl07PWaU7-lMNF6WZVgXXXPo2nUmZ0mtLUOzAr2D1tW3z0rVxnVVtUGbn9PJh2KB8uKgg2Uw-20Ta4btDfAHyncaEn5Gu5re8BZ7AyV7ZhGuNLs13JBmQ1BSMkdYXU5PJJbvHbNT2CT8tH3OGSME6SYMs1JiaKN8lzOqopkr6ZZD4Z5HifZ_7THMsKyEDzmbsOB79xgaoZ7zWEfl-sNO2-Xt6y9QP6QI-1Jn6S1EaLkcaP0-5sHUAtB-e6bPNklB2_h5_tHFCR9pTpWGp1TgTy8ncccQi4yKsitQSi508QcjV9S9rgz--femrbUyuIpZmy6wjvJ5168m8uwIAxWTFOQ5JX57ONJ4Ba4wiQY8E8pzDIJEvXCuKr0Iq94VtoEg1ywk8LAP_l4rbJg4EyFW9Bm57YorJNumsVc7-eX_7nD3qM)

| **#** | Interaction | Data  | Transaction Options |
| ----- | --- | --- | --- |
| 1 | FHIR Bundle | A bundle of FHIR resources representing clinical data for a particular patient encounter. Recommended: FHIR IDs are predefined by the PoS to make looking up of saved data easier | [FHIR Transaction POST](https://www.hl7.org/fhir/http.html#transaction) |
| 2 | Translate terminology codes | The IOL or a mediator uses TS workflows to transalate any necessary codes | Any TS workflows necessary |
| 3 | Extract Patient Resource | | |
| 4 | POST Patient (FHIR format) | FHIR Patient resource | [Create Patient Demographic Record Workflow](../patient-identity-management-workflows/create-patient-demographic-record-workflow-1.md) |
| 5 | Create a new record, if matches to existing source id auto link else run linking | | |
| 6 | Record ID | | |
| 7 | Lookup stub patient resource | | |
| 8 | Return patient or NULL | | |
| 9 | Modify bundle (Strip Patient Demographics, add CR ref with Record ID to Patient.link, retain original Patient.id (uuid)) | | |
| 10 | Modify bundle (Replace patient resource in bundle with SHR (FHIR Server) copy retaining Patient.link, add additional CR ref with Record ID to Patient.link) | | |
| 11 | POST Modifed FHIR Bundle | FHIR Bundle | [FHIR Transaction POST](https://www.hl7.org/fhir/http.html#transaction) |
| 12 | Validate FHIR profiles, terminology, facility and patient references | | |
| 13 | Response | | |
| 14 | Response | | |
