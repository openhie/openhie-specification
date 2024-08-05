# Query Patient-level Clinical Data Workflow (FHIR native)

This transaction allows a point of service (PoS) system to save patient-level clinical data to the SHR. The transaction is verified and validated against necessary metadata before it is saved in the SHR. The following sequence diagram shows the steps involved.

| **Workflow Maturity**         | <p><img src="https://lh6.googleusercontent.com/Kxkqfa92YGW3mIOmWio0Twi4YLMA92z6mL1MuFzkx4AWS5CX5zbzWid5z4p2W-e6O66llKpaU0r6lzwyXfhbIiWmkVEuPDy6stX5x5L8uC2DkEXs6qUFX-7xxXTlb9hbkg" alt=""></p><p><strong>Newly Defined</strong></p> | <ul><li><strong>Workflow is newly defined</strong></li><li><strong>Initial implementations are being implemented</strong></li></ul>  |
| --- | --- | --- |
| Standards |  |  |
| Assumptions and Prerequisites |  | <ul><li>The PoS system is a trusted application known by the HIE and it is registered with the interoperability layer to be able to send and receive data securely (<a href="https://wiki.ohie.org/display/documents/Common+message+security+workflow">Common message security workflow</a>).</li> |
| Actors |  | <ul><li>PoS - The point of care system that captures a patient's clinical encounter, it is responsible for sending clinical data on to the HIE.</li><li>IL - Mediates the transactions between the PoS system and the infrastructure services to facilitate easier interoperability.</li><li>CR - The source of truth for patient demographic and identifier detail. It is able to be queried using an identifier to find the enterprise identifier for a particular person.</li><li>FR - The source of truth for facility information. It is able to be queried for details about a particular facility by ID.</li><li>SHR - Stored patients clinical information. It is able to receive and store patient clinical documents.</li></ul>    |

## **Interaction Description**

The following is a description of the interaction steps. The specific FHIR query that is used isn't strictly specified as this could be any necessary query conformant to the FHIR API that the PoS in the current implementation finds useful. Instead these interaction describe generic behavior for the HIE to support to ensure patient potential multiple identities are considered and resolved.

[![](https://mermaid.ink/img/pako:eNp9Us1LwzAU_1ceOSnUg5-HHgZSlQ0m1vZoe4jN23ysTWqaDMbY_-7bsg3Mppck_PL7Inlr0RiFIhUDfnvUDT6RnFvZVRqgl9ZRQ73UDnJTxtDkbRpDWREj5biAi5fxpIAS7RLtZaW3FLa7Go3YIYWP6xrePdoV7GiP-WRLkI2jpXR4SOGNBVnB_JsapsYsfM9BjpBDSPFKfB5-SUObrDgm3daQn5UojEQh7qQ8e9zFbRNwckF6DqSd4fDGePaXbftXrTNPAqfgsfR9HaIKHHqjB4z6nnUL9YP-oYbMdJ-kEezeYoCZsdD51lHfYtQzaPmD0n9zmSYS0aHtJCmen_X2vhLuCzusRMpHJe2iEpXeMM_3ikXPipyxIp3JdsBESO9MudKNSJ31eCDtB_DIwp3oNUzpblg3P5jK5Xs?type=png)](https://mermaid.live/edit#pako:eNp9Us1LwzAU_1ceOSnUg5-HHgZSlQ0m1vZoe4jN23ysTWqaDMbY_-7bsg3Mppck_PL7Inlr0RiFIhUDfnvUDT6RnFvZVRqgl9ZRQ73UDnJTxtDkbRpDWREj5biAi5fxpIAS7RLtZaW3FLa7Go3YIYWP6xrePdoV7GiP-WRLkI2jpXR4SOGNBVnB_JsapsYsfM9BjpBDSPFKfB5-SUObrDgm3daQn5UojEQh7qQ8e9zFbRNwckF6DqSd4fDGePaXbftXrTNPAqfgsfR9HaIKHHqjB4z6nnUL9YP-oYbMdJ-kEezeYoCZsdD51lHfYtQzaPmD0n9zmSYS0aHtJCmen_X2vhLuCzusRMpHJe2iEpXeMM_3ikXPipyxIp3JdsBESO9MudKNSJ31eCDtB_DIwp3oNUzpblg3P5jK5Xs)

| **#** | Interaction | Data  | Transaction Options |
| ----- | --- | --- | --- |
| 1 | Query FHIR API | Any conformant FHIR Query parameters | [Any FHIR Read Interaction](https://www.hl7.org/fhir/http.html#read) |
| 2 | Lookup patient identities | Known Patient ID | Query Patient Demographic Records by Identifier Workflow |
| 3 | Patient identities | | |
| 4 | Query FHIR API, taking into account all identities | Any conformant FHIR Query parameters | [Any FHIR Read Interaction](https://www.hl7.org/fhir/http.html#read) |
| 5 | FHIR Response | | |
| 6 | Combine responses for multiple identities | | |
| 7 | FHIR Response | | |
