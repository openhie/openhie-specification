# OpenHIE Health Worker Registry (HWR)

The Health Worker Registry serves as the central authority for maintaining the unique identities of health workers within a country. The Health Worker Registry is a database containing a minimum dataset of details of all health workers working in both the public and private sectors. With multiple and disparate sources of data on health workers, it is a complex task to pull together and maintain a master and canonical list of all health workers in a country. The health worker registry seeks to reduce the complexity of this task by:

* Pulling the minimum dataset of health workforce information from the various source data systems.&#x20;
* Merging the source data systems into an authoritative registry of health workers according to a data governance policy.&#x20;
* Allowing queries of health worker information by client systems.

See also [Non-Functional Requirements](non-functional-requirements.md).

## **OpenHIE HWR Workflow Requirements**

A [core principle of the OpenHIE architecture](https://wiki.ohie.org/display/resources/Architectural+Principals) is to allow the various infrastructure services (such as the HWR) to be interchangeable. To support this, the [OpenHIE Standards and Profiles](https://wiki.ohie.org/display/documents/OpenHIE+Standards+and+Profiles) used by the Health Worker Registry are outlined in the workflows below.

To be an OHIE HWR component, the HWR application must be able to support the OHIE workflows listed below. Implementations may support only the workflows needed to support their use case:

| #                                                                                                                             | **HWR Workflows (Described in detail in the later part of this document)**                                                                               | **Recommendation/ Requirement**                         |
| ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| \*\*\*\*[**HWWF-1**](../introduction/care-services-discovery/query-health-worker-and-or-facility-records-workflow.md)\*\*\*\* | [Query health worker and/or facility records workflow.](../introduction/care-services-discovery/query-health-worker-and-or-facility-records-workflow.md) | Requirement (One of HWWF-1 or HWWF-2 must be supported) |
| \*\*\*\*[**HWWF-2**](../introduction/care-services-discovery/query-care-services-records-workflow.md)\*\*\*\*                 | [Query care services records workflow.](../introduction/care-services-discovery/query-care-services-records-workflow.md)                                 | Requirement (One of HWWF-1 or HWWF-2 must be supported) |
| \*\*\*\*[**HWWF-3**](../introduction/care-services-discovery/search-care-services-workflow.md)\*\*\*\*                        | [Search care services workflow.](../introduction/care-services-discovery/search-care-services-workflow.md)                                               | Recommendation                                          |
| \*\*\*\*[**HWWF-4**](../introduction/care-services-discovery/request-care-services-updates-workflow.md)\*\*\*\*               | [Request care services updates workflow.](../introduction/care-services-discovery/request-care-services-updates-workflow.md)                             | Requirement                                             |

## **OpenHIE HWR Functional Requirements**

| **#**      | **HWR Functional Requirement**                                                                                                                                                                             | **Recommendation/ Requirement** |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| **HWRF-1** | The system shall support the ability to query source data systems for updates to health worker data.                                                                                                       | Required                        |
| **HWRF-2** | The system shall support the ability to retain received updates from source data systems.                                                                                                                  | Required                        |
| **HWRF-3** | The system shall support the ability to respond to queries on health worker data that has been stored.                                                                                                     | Required                        |
| **HWRF-4** | The system should be able to send updates to upstream data repositories (such as an InterLinked Registry).                                                                                                 | Recommended                     |
| **HWRF-5** | The system should support the ability to maintain old versions of health worker data when it has been updated.                                                                                             | Recommended                     |
| **HWRF-6** | The system should support the collection of data for the following minimum dataset: [https://www.who.int/hrh/statistics/minimun\_data\_set/en/](https://www.who.int/hrh/statistics/minimun\_data\_set/en/) | Recommended                     |
| **HWRF-7** | The system should have flexible standards-based APIs, based on CSD or mCSD                                                                                                                                 | Required                        |
