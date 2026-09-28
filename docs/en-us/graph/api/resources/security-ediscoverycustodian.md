<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# ediscoveryCustodian resource type

Namespace: microsoft.graph.security

In the context of eDiscovery, represents a user and all of their digital assets, such as email and documents.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-custodians?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) collection | Get a list of the [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-post-custodians?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) | Create a new [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-get?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) | Read the properties and relationships of an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) object. |
| [Update index](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-updateindex?view=graph-rest-1.0) | Triggers a indexOperation to make a custodian and associated sources searchable. |  |
| [Activate](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-activate?view=graph-rest-1.0) | None | Re-activate a custodian from a case. |
| [Release](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-release?view=graph-rest-1.0) | None | Release a custodian from a case. |
| [Apply hold](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-applyhold?view=graph-rest-1.0) | None | Start the process of applying hold to eDiscovery custodians. |
| [Remove hold](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-removehold?view=graph-rest-1.0) | None | Start the process of removing hold from eDiscovery custodians. |
| [Get last index operation](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-list-lastindexoperation?view=graph-rest-1.0) | [microsoft.graph.security.ediscoveryIndexOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryindexoperation?view=graph-rest-1.0) collection | Get a list of the [ediscoveryIndexOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryindexoperation?view=graph-rest-1.0) associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| **Site sources** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-list-sitesources?view=graph-rest-1.0) | [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) collection | Get a list of the [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) objects associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-post-sitesources?view=graph-rest-1.0) | [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) | Create a new [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-delete-sitesources?view=graph-rest-1.0) | None | Delete a [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| **Unified group sources** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-list-unifiedgroupsources?view=graph-rest-1.0) | [microsoft.graph.security.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) collection | Get a list of the [unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) objects associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-post-unifiedgroupsources?view=graph-rest-1.0) | [microsoft.graph.security.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) | Create a new [unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-unifiedgroupsource-delete?view=graph-rest-1.0) | None | Delete a [unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| **User sources** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-list-usersources?view=graph-rest-1.0) | [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) collection | Get a list of the [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) objects associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) or [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-post-usersources?view=graph-rest-1.0) | [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) | Create a new [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-delete-usersources?view=graph-rest-1.0) | None | Delete a [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| acknowledgedDateTime | DateTimeOffset | Date and time the custodian acknowledged a hold notification. |
| createdDateTime | DateTimeOffset | Date and time when the custodian was added to the case. |
| displayName | String | Display name of the custodian. |
| email | String | Email address of the custodian. |
| holdStatus | microsoft.graph.security.dataSourceHoldStatus | The hold status of the custodian.The possible values are: `notApplied`, `applied`, `applying`, `removing`, `partial` |
| id | String | The ID for the custodian in the specified case. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time the custodian object was last modified |
| releasedDateTime | DateTimeOffset | Date and time the custodian was released from the case. |
| status | microsoft.graph.security.custodianStatus | Status of the custodian. The possible values are: `active`, `released`. |

### custodianStatus values

| Name | Description |
| :--- | --- |
| active | Custodian is an active part of the case. |
| released | Custodian is released from the case. |

### custodianHoldStatus values

| Name | Description |
| :--- | --- |
| notApplied | The custodian is not on Hold \(all sources in it are not on hold\). |
| applied | The custodian is on Hold \(all sources are on hold\). |
| applying | The custodian is in applying hold state \(applyHold operation triggered\). |
| removing | The custodian is in removing the hold state\(removeHold operation triggered\). |
| partial | The custodian is in mixed state where some sources are on hold and some not on hold or error state. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| lastIndexOperation | [microsoft.graph.security.ediscoveryIndexOperation](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryindexoperation?view=graph-rest-1.0) | Operation entity that represents the latest indexing for the custodian. |
| siteSources | [microsoft.graph.security.siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) collection | Data source entity for SharePoint sites associated with the custodian. |
| unifiedGroupSources | [microsoft.graph.security.unifiedGroupSource](https://learn.microsoft.com/en-us/graph/api/resources/security-unifiedgroupsource?view=graph-rest-1.0) collection | Data source entity for groups associated with the custodian. |
| userSources | [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) collection | Data source entity for a the custodian. This is the container for a custodian's mailbox and OneDrive for Business site. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryCustodian",
  "id": "String (identifier)",
  "status": "String",
  "holdStatus": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "releasedDateTime": "String (timestamp)",
  "displayName": "String",
  "createdDateTime": "String (timestamp)",
  "email": "String",
  "acknowledgedDateTime": "String (timestamp)"
}
```
