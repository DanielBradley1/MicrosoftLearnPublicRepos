<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# userSource resource type

Namespace: microsoft.graph.security

The container for a user's mailbox and OneDrive for Business site.

Inherits from [dataSource](https://learn.microsoft.com/en-us/graph/api/resources/security-datasource?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| **eDiscovery custodian** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-list-usersources?view=graph-rest-1.0) | [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) collection | Get a list of the [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) objects associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0) or [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-post-usersources?view=graph-rest-1.0) | [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) | Create a new [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoverycustodian-delete-usersources?view=graph-rest-1.0) | None | Delete a [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) object associated with an [ediscoveryCustodian](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoverycustodian?view=graph-rest-1.0). |
| **eDiscovery hold policy** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-list-usersources?view=graph-rest-1.0) | [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) collection | Get a list of the [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) objects associated with an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-post-usersources?view=graph-rest-1.0) | [microsoft.graph.security.userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) | Create a new [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-delete-usersources?view=graph-rest-1.0) | None | Delete a [userSource](https://learn.microsoft.com/en-us/graph/api/resources/security-usersource?view=graph-rest-1.0) object associated with an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created the **userSource**. |
| createdDateTime | DateTimeOffset | The date and time the **userSource** was created. |
| displayName | String | The display name associated with the mailbox and site. |
| email | String | Email address of the user's mailbox. |
| holdStatus | microsoft.graph.security.dataSourceHoldStatus | The hold status of the **userSource**. The possible values are: `notApplied`, `applied`, `applying`, `removing`, `partial`. |
| id | String | The ID of the **userSource**. This isn't the ID of the actual group. |
| includedSources | microsoft.graph.security.sourceType | Specifies which sources are included in this group. The possible values are: `mailbox`, `site`. |
| siteWebUrl | String | The URL of the user's OneDrive for Business site. Read-only. |

### userSourceHoldStatus values

| Name | Description |
| :--- | --- |
| notApplied | The userSource isn't on hold \(all sources in it aren't on hold\). |
| applied | The userSource is on hold \(all sources are on hold\). |
| applying | The userSource is in applying hold state \(applyHold operation triggered\). |
| removing | The userSource is in removing the hold state \(removeHold operation triggered\). |
| partial | The userSource is in mixed state where some sources are on hold and some not on hold or error state. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.userSource",
  "id": "String (identifier)",
  "displayName": "String",
  "holdStatus": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "email": "String",
  "includedSources": "String",
  "siteWebUrl": "String"
}
```
