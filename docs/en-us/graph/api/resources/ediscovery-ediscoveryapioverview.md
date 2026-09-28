<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-ediscoveryapioverview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# Use the Microsoft Graph eDiscovery API

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The Microsoft Graph APIs for eDiscovery enable organizations to automate repetitive tasks and integrate with their existing eDiscovery tools to build repeatable workflows that industry regulations might require. You can use the eDiscovery APIs to help with your legal needs.

Important

The Microsoft Graph APIs for eDiscovery are intended for the use of eDiscovery operations for litigation, investigation, and regulatory requests. These APIs shouldn't be used as a substitute for journaling data out of the Microsoft 365 system or any other mass download.

Note

Entitlement and feature availability for the eDiscovery APIs in Microsoft Graph are determined by Microsoft Purview eDiscovery configuration and service-side enablement. For current licensing and capability guidance, see the [Microsoft Purview eDiscovery documentation](https://learn.microsoft.com/en-us/purview/edisc).

The eDiscovery API is defined in the OData subnamespace, microsoft.graph.ediscovery. The API includes the following key entities.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

| Name | Type | Use case |
| :--- | :--- | :--- |
| Case | [microsoft.graph.ediscovery.case](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-case?view=graph-rest-beta) | The container for all eDiscovery objects including custodians, holds, searches, review sets, and exports. |
| Custodian | [microsoft.graph.ediscovery.custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) | A person and the data they have administrative control over. When custodians are identified, *Advanced eDiscovery* can hold, search, cull, and export their data. For details, see [Work with custodians and noncustodial data sources in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/managing-custodians). |
| Legal hold | [microsoft.graph.ediscovery.legalHold](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-legalhold?view=graph-rest-beta) | Used to hold content for litigation and legal purposes. Legal holds shouldn't be confused with or used as retention holds, which are typically used to comply with government or industry regulations. To learn more, see [Manage holds in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/managing-holds). |
| Review set | [microsoft.graph.ediscovery.reviewSet](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewset?view=graph-rest-beta) | A static set of electronically stored information collected for use in a litigation, investigation, or regulatory request. |
| Review set query | [microsoft.graph.ediscovery.reviewSetQuery](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-reviewsetquery?view=graph-rest-beta) | Used to discover, cull, review, and tag [ESI](https://en.wikipedia.org/wiki/Electronically_stored_information_\(Federal_Rules_of_Civil_Procedure\)) with the goal of production to the requestor or opposing counsel. |
| Source collection | [microsoft.graph.ediscovery.sourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sourcecollection?view=graph-rest-beta) | Commonly known as searches, allow you to collect data from the Microsoft 365 live services such as Exchange, SharePoint, and Teams. Source collections can be added to a review set to further cull and eventually export data relevant to your case. For details, see [Collect data for a case in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/collecting-data-for-ediscovery). |
| Tags | [microsoft.graph.ediscovery.tag](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-tag?view=graph-rest-beta) | Used in a review set during review or culling to cull responsive data from non-responsive data, identify privileged content, or generally aid in the review process. To learn more, see [Tag documents in a review set in Advanced eDiscovery](https://learn.microsoft.com/en-us/microsoft-365/compliance/tagging-documents). |
