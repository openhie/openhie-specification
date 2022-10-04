# OpenHIE Terminology Service (TS)

The Terminology Services component of the [OpenHIE Architecture](https://wiki.ohie.org/pages/viewpage.action?pageId=8454157) provides a centralized source for the HIE’s standards and definitions, including terminologies, ontologies, dictionaries, code systems, and value sets.  Other HIE components can use these standards and definitions to normalize clinical data and achieve consistent aggregation and reporting. &#x20;

By using Terminology Services, an HIE can achieve semantic interoperability of its data. Semantic interoperability (or interoperability of meaning) enables accurate, consistent reporting and aggregation of clinical data. It also enables accurate exchange of information among members of the provider community, including labs, clinics, pharmacies, hospitals and imaging centers, which leads to improved patient care decisions.

Benefits of the use of a Terminology Service include:

* **Standard Data:** Using common terminology is vital for knowledge sharing over multiple locations. National and international code systems and value sets should be readily available for validation, comparison, and aggregation with local data.
* **Improved Care:** Accurate and consistent data collection improves patient care analysis. Comparable patient data within and between patient populations leads to more consistent care delivery.
* **Better Reporting:** Standardized data element representations result in consistent and accurate reporting.
* **Coordinated Care:** Consistent and comparable analysis of healthcare utilization data leads to more informed decisions about resource allocation.

See also [Non-Functional Requirements](non-functional-requirements.md).&#x20;

## OpenHIE TS Workflow Requirements&#x20;

A Terminology Service exposes a set of run-time functions (services) that support other OHIE components. These Terminology Service functions are typically actions found in the primary OHIE Workflows (see example below). Four primary functions have been identified. Depending upon the specific Workflows required in an implementation, not all of these functions may be required, but an OHIE-compliant Terminology Service should support all of these features.

To be an OHIE TS component, the TS application must be able to support the OHIE workflows listed below.  Implementations may support only the workflows needed to support their use case. All of the required functions below are to be implemented using the associated HL7 FHIR Terminology Service specifications, e.g. Resources and Operations. These workflows also conform to the IHE Infrastructure Technical Framework Supplement - Sharing Value Sets, Codes, and Maps (SVCM) specification.

| #                                                                                            | **TS Workflows (Described in detail in the later part of this document)**                        | **Recommendation/ Requirement** |
| -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------- |
| ****[**TSWF-1**](../introduction/terminology-service-workflow/verify-code-existence.md)****  | [Verify Code Existence](../introduction/terminology-service-workflow/verify-code-existence.md)   | Requirement                     |
| ****[**TSWF-2**](../introduction/terminology-service-workflow/verify-code-membership.md)**** | [Verify Code Membership](../introduction/terminology-service-workflow/verify-code-membership.md) | Requirement                     |
| ****[**TSWF-3**](../introduction/terminology-service-workflow/expand-value-set.md)****       | [Expand Value Set](../introduction/terminology-service-workflow/expand-value-set.md)             | Requirement                     |
| ****[**TSWF-4**](../introduction/terminology-service-workflow/query-concept-maps.md)****     | [Query Concept Map](../introduction/terminology-service-workflow/query-concept-maps.md)          | Requirement                     |
| ****[**TSWF-5**](../introduction/terminology-service-workflow/query-code-systems.md)****     | [Query Code System](../introduction/terminology-service-workflow/query-code-systems.md)          | Requirement                     |
| ****[**TSWF-6**](../introduction/terminology-service-workflow/query-value-set.md)****        | [Query Value Set](../introduction/terminology-service-workflow/query-value-set.md)               | Requirement                     |
| ****[**TSWF-7**](../introduction/terminology-service-workflow/lookup-code.md)****            | [Lookup Code](../introduction/terminology-service-workflow/lookup-code.md)                       | Requirement                     |
| ****[**TSWF-8**](../introduction/terminology-service-workflow/translate-code.md)****         | [Translate Code](../introduction/terminology-service-workflow/translate-code.md)                 | Requirement                     |

## OpenHIE TS Functional Requirements&#x20;

| #          | **TS Functional Requirements**                                                                                                                                                                                  | **Recommendation / Requirement** |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| **TSF-1**  | The TS shall support import of local (e.g., local lab codes)  and standard code systems (e.g., LOINC).                                                                                                          | Requirement                      |
| **TSF-2**  | The TS shall allow for export of local (e.g. local lab codes) and standard code systems (e.g., LOINC).                                                                                                          | Requirement                      |
| **TSF-3**  | The TS should support versioning of code systems - storing and making multiple versions of a code system available via terminology services.                                                                    | Recommendation                   |
| **TSF-4**  | The TS should support versioning of value sets - storing and making multiple versions of a value set available via terminology services.                                                                        | Recommendation                   |
| **TSF-5**  | The TS shall allow import of value set definitions. The import format may vary from a text file containing a list of codes to an FHIR Value Set resource in XML or JSON format.                                 | Requirement                      |
| **TSF-6**  | The TS shall allow for export of value sets definitions. The export format may vary from a text file containing a list of codes to an FHIR Value Set resource in XML or JSON format.                            | Requirement                      |
| **TSF-7**  | The TS shall allow for the import of value set expansions. The import format may vary from a text file containing a list of codes to an FHIR Value Set resource in XML or JSON format.                          | Requirement                      |
| **TSF-8**  | The TS shall allow for export of value sets expansions. The export format may vary from a text file containing a list of codes to an FHIR Value Set resource in XML or JSON format.                             | Requirement                      |
| **TSF-9**  | Allow for the import of relationships between codes (i.e., concept maps). The import format may vary from a text file containing source and target codes to an FHIR Concept Map resource in XML or JSON format. | Requirement                      |
| **TS -10** | Allow for the export of relationships between codes (i.e., concept maps). The export format may vary from a text file containing source and target codes to an FHIR Concept Map resource in XML or JSON format. | Requirement                      |
| **TSF-11** | Expose services that allow for the retrieval of a code, and additional information about the code such as definition and status, from a particular code system (and code system version if provided).           | Requirement                      |
| **TSF-12** | Expose services that allow for the validation of a code (i.e., does the code exist) against a particular code system (and code system version if provided).                                                     | Requirement                      |
| **TSF-13** | Expose services that utilize concept maps to retrieve a target code given a source code within the concept map.                                                                                                 | Requirement                      |
