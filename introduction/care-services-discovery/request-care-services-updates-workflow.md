# Request Care Services Updates Workflow

Workflow for a point of service application to query a Care Services Registry or directory for updates to health workers, facilities, organizations, and/or the services provided by each.

| **Workflow Maturity**         | <p><img src="https://lh3.googleusercontent.com/5pqeaiKmzar1ArIa8oQG4D_pt1AUs6-4_d5KLJXFLpkp1PdN4eYtUD5YcMO0YNTHEH4OkUp5Jom_Gy56jgz-2o5kGTV9QtIBtg79TYH2wWecLI6PzT4uXwuBlbBKPagbDw" alt=""></p><p>  <strong>Maturing</strong></p> | <p><strong></strong></p><ul><li>Workflow is defined and ARB Approved</li><li>Workflow is supported by emerging IHE mCSD standard</li></ul>                                                                   |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Standards\*                   |                                                                                                                                                                                                                                  | Mobile Care Services Discovery (mCSD): ftp://ftp.ihe.net/DocumentPublication/CurrentPublished/ITInfrastructure/IHE\_ITI\_Suppl\_mCSD.pdf                                                                     |
| Assumptions and Prerequisites |                                                                                                                                                                                                                                  | <p></p><p>A Care Services Registry shall have one or more of the following resources:</p><ul><li>Location</li><li>Practitioner and PractitionerRole</li><li>Organization</li><li>HealthcareService</li></ul> |
| Actors                        |                                                                                                                                                                                                                                  | <p></p><ul><li>ILR= InterLinked Registry, mCSD Care Services Update Consumer</li><li>CSR = Any Care Services Registry (e.g. HWR or FR), mCSD Care Services Update Supplier</li></ul>                         |

## **Interaction Description**&#x20;

The following is a description of the interaction steps.&#x20;

![](https://lh5.googleusercontent.com/Qo99bmR5cItDA89ePqPqp8OUxcZx6pydhwRUhP64aIOCzmMYLqIQTWvJLXUhV1SQ7L5VsjVr86SW30sD9zWu2EHVLRHwLw7K9-BquP4HvSRuxOQAT\_kZLlx0IuEerASdaw)

| **#** | **Interaction**               | **Data / Notes**                                                                                        | **Transaction Options**                  |
| ----- | ----------------------------- | ------------------------------------------------------------------------------------------------------- | ---------------------------------------- |
| 1     | Request care services updates | HTTP GET Request with optional date parameter.  Can be for any supported resources.                     | \[ITI-91] Request Care Services Updates  |
| 2     | Return updated care services  | HTTP response with FHIR Bundle of matching resources or an error if an invalid request or server error. | \[ITI-91] Request  Care Services Updates |
