<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# custodian resource type

Namespace: microsoft.graph.ediscovery

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The eDiscovery APIs in the microsoft.graph.eDiscovery subnamespace are deprecated. Use the new [eDiscovery APIs under microsoft.graph.security subnamespace](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview#ediscovery).

In the context of eDiscovery, represents a user and all of their digital assets, such as email and documents.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-list-custodians?view=graph-rest-beta) | [microsoft.graph.ediscovery.custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) collection | Get a list of **custodian** objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/ediscovery-case-post-custodians?view=graph-rest-beta) | [microsoft.graph.ediscovery.custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) | Create a new **custodian** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-get?view=graph-rest-beta) | [microsoft.graph.ediscovery.custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) | Read the properties and relationships of a **custodian** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-update?view=graph-rest-beta) | [microsoft.graph.ediscovery.custodian](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-custodian?view=graph-rest-beta) | Update the properties of a **custodian** object. |
| [Release](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-release?view=graph-rest-beta) | None | Release a custodian from a case. |
| [Activate](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-activate?view=graph-rest-beta) | None | Reactivate a custodian that has been released from a case and make them part of the case again. |
| [List site sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-list-sitesources?view=graph-rest-beta) | [microsoft.graph.ediscovery.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta) collection | Get the **siteSource** resources associated with the custodian. |
| [Create site sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-post-sitesources?view=graph-rest-beta) | [microsoft.graph.ediscovery.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta) | Create a new **siteSource** object. |
| [List unified group sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-list-unifiedgroupsources?view=graph-rest-beta) | [microsoft.graph.ediscovery.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-unifiedgroupsource?view=graph-rest-beta) collection | Get the list of **unifiedGroupSource** resources associated with the custodian. |
| [Create unified group sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-post-unifiedgroupsources?view=graph-rest-beta) | [microsoft.graph.ediscovery.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-unifiedgroupsource?view=graph-rest-beta) | Create a new **unifiedGroupSource** object. |
| [List user sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-list-usersources?view=graph-rest-beta) | [microsoft.graph.ediscovery.userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) collection | Get the list of **userSource** resources associated with the custodian. |
| [Create user sources](https://learn.microsoft.com/en-us/graph/api/ediscovery-custodian-post-usersources?view=graph-rest-beta) | [microsoft.graph.ediscovery.userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) | Create a new **userSource** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| acknowledgedDateTime | DateTimeOffset | Date and time the custodian acknowledged a hold notification. |
| applyHoldToSources | Boolean | Identifies whether a custodian's sources were placed on hold during creation. |
| createdDateTime | DateTimeOffset | Date and time when the custodian was added to the case. |
| displayName | String | Display name of the custodian. |
| email | String | Email address of the custodian. |
| id | String | The ID for the custodian in the specified case. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the custodian object was last modified |
| releasedDateTime | DateTimeOffset | Date and time the custodian was released from the case. |
| status | microsoft.graph.ediscovery.custodianStatus | Status of the custodian. The possible values are: `active`, `released`. |

### custodianStatus values

| Member | Description |
| :--- | --- |
| active | Custodian is an active part of the case. |
| released | Custodian is released from the case. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| siteSources | [microsoft.graph.ediscovery.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-sitesource?view=graph-rest-beta) collection | Data source entity for SharePoint sites associated with the custodian. |
| unifiedGroupSources | [microsoft.graph.ediscovery.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-unifiedgroupsource?view=graph-rest-beta) collection | Data source entity for groups associated with the custodian. |
| userSources | [microsoft.graph.ediscovery.userSource](https://learn.microsoft.com/en-us/graph/api/resources/ediscovery-usersource?view=graph-rest-beta) collection | Data source entity for a the custodian. This is the container for a custodian's mailbox and OneDrive for Business site. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ediscovery.custodian",
  "email": "String",
  "applyHoldToSources": "Boolean",
  "status": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "releasedDateTime": "String (timestamp)",
  "acknowledgedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "displayName": "String"
}
```
