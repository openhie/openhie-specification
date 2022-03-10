# Workflow (Exchange) Specification

OpenHIE workflows are the technical data exchange patterns for sharing health data between one or more of the [OpenHIE Architecture](https://wiki.ohie.org/pages/viewpage.action?pageId=8454157) components and/or other health information systems. As specified in the process documented above, the OpenHIE workflows have been vetted and agreed upon by the OpenHIE [Architecture Review Board](https://wiki.ohie.org/display/documents/Architecture+Review+Board+Members%2C+Responsibilities+and+Deliverables). The purpose of this section is to document the workflow specifications for OpenHIE. New workflows are being created and additional standards such as FHIR may not yet be incorporated and this type of work in progress may be found on the OpenHIE wiki. In addition, you are invited to join our processes and contribute new workflows for the next release.

For each workflow the following is documented:

* Maturity - Each workflow’s maturity is subjectively documented based upon the following factors: &#x20;
  * The workflow is defined and ARB approved
  * The workflow is supported by standards
  * The maturity of the underlying standards or profiles
  * The number of implementations&#x20;
* Standards - IHE profiles that are the building blocks for the OpenHIE workflows.  These IHE Profiles represent the conformance-testable descriptions of how actors in an interoperable data exchange must behave. The maturity of the underlying FHIR standards, themselves, is identified on the front page of the IHE Profile specification itself. FHIR resource list can be displayed and sorted by maturity; this list is found, here: [https://www.hl7.org/fhir/resourcelist.html](https://www.hl7.org/fhir/resourcelist.html). (The FHIR maturity levels are defined, here: [https://www.hl7.org/fhir/versions.html#maturity](https://www.hl7.org/fhir/versions.html#maturity)).
* Assumptions and Prerequisites - Conditions that are expected to be in place to support the workflow. &#x20;
* Actors - The systems or HIE components that have roles in the data exchange process being specified. &#x20;
* Interaction diagram - The visual description of how the data moves between systems. &#x20;
* Interaction diagram steps - Details explaining the steps in the interaction diagram. &#x20;
