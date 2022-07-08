# Query Concept Maps

&#x20;This transaction allows a PoS, or any OHIE component, to access terminological information in the terminology service to query for Concept Maps.  A typical example would be to request the set of Concept Maps whose target Code System is SNOMED CT. Mapping is frequently required when patient data is collected using Concepts/Codes from one Code System but the data must be reported or aggregated, say for decision support, in a different Code System. The set of such associated Concepts, usually for a specific use-case, are stored in the Terminology Service in a FHIR Resource called a ConceptMap.

Both external systems and systems inside the HIE may perform this transaction directly with the TS. The sequence diagram below shows the steps that occur for a system using this transaction.  &#x20;

1. Query Concept Maps: What Concept Maps have a map target of 'SNOMED CT''?

| **Workflow Maturity**         | <p><img src="https://lh5.googleusercontent.com/Vp6XBRGu-U_Dmd5EKNpCZvEEum0CxOcHOj9NgHh8UMMNLMlXHmLcUE_YWueDRr4uqWLzpPfzSBLJ2k33XQIelLypjQ4wyrD17-t33GtLa8fFxW9AYDvXhiJmBl4VaLgKDg" alt=""></p><p>   <strong>Mature</strong></p> | <p></p><ul><li><strong>One or more OpenHIE implementations of this workflow exist  in one or more countries</strong></li><li><strong>Workflow is defined and ARB approved</strong></li><li><strong>Workflow is supported by mature standards</strong></li></ul> |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Standards\*                   |                                                                                                                                                                                                                                 | <p></p><ul><li>One or more OpenHIE implementations of this workflow exist  in one or more countries</li><li>Workflow is defined and ARB approved</li><li>Workflow is supported by mature standards</li></ul>                                                    |
| Assumptions and Prerequisites |                                                                                                                                                                                                                                 | The required Concept Maps have been preloaded into the Terminology Service.                                                                                                                                                                                     |
| Actors                        |                                                                                                                                                                                                                                 | <p></p><ul><li>PoS - The point-of-service system  or other HIE component that is that is querying for Concept Maps.   </li><li>TS - Stores the curated, official version of the Concept Maps for the health system.</li></ul>                                   |

## Interaction Description&#x20;

The following is a description of the interaction steps.

![](https://lh4.googleusercontent.com/lMBBRqFL2VgXeCrFBOPH-K-sDVo4hHqwW7gP7wxjyYAwbDHAITnWIGb3eddt6CQDVPCGPq3V56kCGENMV17f0WjgWxJ7R-XWpAX\_l2nKoEGMr-\_GDoPEd927PHERFR27QQ)

| # | Interaction                | Data                                                                                                                                           | Transaction Options      |
| - | -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------ |
| 1 | Query Concept Map request  | <p>The Concept Map search request is triggered by a PoS or other HIE component.</p><p>Input: A set of FHIR search parameters.</p>              | FHIR ConceptMap Resource |
| 2 | Query Concept Map response | <p>The response is sent back to the requesting system. </p><p>Output: a Bundle of ConceptMap Resources that satisfy the search parameters.</p> | FHIR ConceptMap Resource |

##
