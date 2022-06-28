# Architecture

## Overview&#x20;

A Health Information Exchange (HIE), the shared infrastructure in the large gray box of the OpenHIE Architecture Diagram makes the sharing of health data across information systems possible. Like a universal translator, an HIE normalizes data and secures the transmission of health information throughout databases, between facilities, and across regions or countries.

OpenHIE’s architecture is made up of software components, all interacting/interoperating to ensure that health information from various point-of-service systems is gathered into a health information exchange. To accomplish this, the exchange normalizes the context in which health information is created across multiple dimensions including:&#x20;

1. Who received health services&#x20;
2. Who provided the services
3. Where the services were received
4. What particular care and services were received&#x20;
5. What products may have been involved in treatment
6. Who has financial responsibility

This separation of concerns supports quality, safety, and continuity of care, and facilitates the appropriate use of information needed for population health and metrics calculation.

## OpenHIE Architecture Diagram

![](../.gitbook/assets/ohie\_diagram\_2021-09-29.png)

## Architecture Component Descriptions&#x20;

### Business Domain Services&#x20;

Business Domain Services are Health Exchange components that are designed to support specific health system business domains and would have the potential to combine data Health Exchange data from multiple point-of-care systems. &#x20;

1. **Logistics Management Information Service (LMIS)** - A Logistics Management Information System (LMIS) is an IT system that plays a central role in enabling commodity visibility and operational management of a wide-area supply chain operation.  Typically the commodities in this supply chain are health-related, the organization that sponsors the system is a department or agency under a government's health ministry and the operation is carried out at scale for an entire region or even an entire nation. An LMIS typically bridges the health and supply chain operations by enabling re-supply workflows for clinical locations and the vertical programs targeting families of commodities, as well as interfacing with supplier's IT systems to ensure the re-supply process is fulfilled as needed.  Particular LMIS tools may have additional capabilities that enhance these re-supply workflows and/or add to the maturity of the wider supply chain operation.\

2. A [**Shared Health Record** ](https://wiki.ohie.org/display/SUB/Shared+Health+Record+Community)(SHR) is a repository containing the normalized version of content created within the community, after being validated against each of the previous registries.  It is a collection of person-centric records for patients with information in the exchange. See also: [What constitutes an OpenHIE SHR?](https://wiki.ohie.org/pages/viewpage.action?pageId=19464697)\

3. A [**Health Management Information Service**](https://wiki.ohie.org/display/SUB/Health+Management+Information+System+Community) (HMIS) stores routinely-collected aggregate health care data, and facilitates their analysis with the goal of improving the quality of health services. See also: [What constitutes an OpenHIE HMIS?](https://wiki.ohie.org/pages/viewpage.action?pageId=30149406)\

4. **Finance and Insurance Service** stores, categorizes and facilitates the administration of centralised claims and finance related data to care provision to patients within the HIE. The service receives claims/financial data from Point of Service applications (including financing applications acting as a point of service interface outside of other PoS systems) and curates the management of them.

### Registry Services&#x20;

Registry Services are Health Exchange Components that are designed to support registries with data that is used by other Health Exchange components. &#x20;

1. A [**Terminology Service**](https://wiki.ohie.org/display/SUB/Terminology+Service+Community) **** serves as a central authority to uniquely identify the clinical activities that occur within the care delivery process by maintaining a terminology set mapped to international standards such as ICD-10, LOINC, SNOMED, and others – “What?” See also:[What constitutes an OpenHIE Terminology Service?](https://wiki.ohie.org/pages/viewpage.action?pageId=30149397)\

2. An enterprise master patient index (EMPI), or [**Client Registry**](https://wiki.ohie.org/display/SUB/Patient+Identity+Management+Community) manages the unique identity of citizens receiving health services with the country – “For whom".  See also: [What constitutes an OpenHIE CR?](https://wiki.ohie.org/pages/viewpage.action?pageId=29593103)\

3. A [**Health Facility Registry**](https://wiki.ohie.org/display/SUB/Facility+Registry+Community) serves as a central authority to uniquely identify all places where health services are administered within the country – “Where?” See also: [What constitutes an OpenHIE Facility Registry?](https://wiki.ohie.org/pages/viewpage.action?pageId=30149404)\

4. A [**Health Worker Registry**](https://wiki.ohie.org/display/SUB/Health+Worker+Registry+Community) is the central authority for maintaining the unique identities of health providers within the country – “By whom." See also:  [What constitutes a HWR?](https://wiki.ohie.org/pages/viewpage.action?pageId=30149401)\

5. [**Product Catalogue** ](https://wiki.ohie.org/display/SUB/Product+Identification+Terminology#ProductIdentificationTerminology-ProductRegistry)**-** Product Catalogue serves as the source of truth about what a Product is within an HIE.  It sources the information for this role through two expected means:  1) as the ongoing result of a process of master data management to properly define and categorize medical products and 2) as derived data on the proper definition and categorization of medical products (e.g. GS1 GDSN).

### Interoperability Services Layer&#x20;

1. **Authentication**- Verification of the credentials of systems sending messages to the interoperability layer.\
   \

2. **Interlinking Service**- Service to link health workers with facilities.\
   \

3. &#x20;A [**Health Interoperability Layer**](https://wiki.ohie.org/display/SUB/Interoperability+Layer+Community) receives all communications from external services within a health geography, and orchestrates message processing among the external systems and the OpenHIE component layer. See also: [What constitutes an OpenHIE IOL?](https://wiki.ohie.org/pages/viewpage.action?pageId=29592925)
4. **Entity Matching**- Process of matching entities to link duplicate records. This can be used to match entities to determine if there are potential matches within a single list or across two lists. This function can be used with any entity, but has been most often used with patient demographic records to link an individual patient’s records from disparate systems or to match facility records across different systems.

### **Point-of-service**

Point-of-service applications such as the OpenMRS electronic medical records (EMR) system and the RapidSMS mHealth application, are used by clinicians and by community health workers to access and update a patient’s person-centric shared health information and to record healthcare transactions.   They share data by interacting with the Health Information Exchange depicted in the larger grey box.  \
\
