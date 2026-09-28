<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunit?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-07 -->

# siteProtectionUnit resource type

Namespace: microsoft.graph

Represents a SharePoint site that has a [SharePoint protection policy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0) applied.

Inherits from [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-siteprotectionunits?view=graph-rest-1.0) | [siteProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunit?view=graph-rest-1.0) collection | Get a list of [siteProtectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionunit?view=graph-rest-1.0) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who created the protection unit. Inherited from [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The time of creation of the protection unit. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains error details if enabling or disabling the protection unit fails. Inherited from [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |
| id | String | Unique identifier of the protection policy associated with this protection unit. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who last modified the protection unit. Inherited from [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The time the protection unit was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |
| offboardRequestedDateTime | DateTimeOffset | The date and time when protection unit offboard was requested. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |
| policyId | String | Unique identifier of the protection policy associated with this protection unit. Inherited from [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |
| protectionSources | protectionSource | Indicates the sources by which a protection unit is currently protected. A protection unit protected by multiple sources is indicated by comma-separated values. The possible values are: `none`, `manual`, `dynamicRule`, `unknownFutureValue`. Inherited from [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |
| siteId | String | Unique identifier of the SharePoint site. |
| siteName | String | Name of the SharePoint site. |
| siteWebUrl | String | The web URL of the SharePoint site. |
| status | [protectionUnitStatus](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0#protectionunitstatus-values) | The individual enablement/disablement/removal status of the protection unit. The possible values are: `protectRequested`, `protected`, `unprotectRequested`, `unprotected`, `removeRequested`, `unknownFutureValue`, `offboardRequested`, `offboarded`, `cancelOffboardRequested`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `offboardRequested`, `offboarded`, `cancelOffboardRequested`. Inherited from [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.siteProtectionUnit",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "offboardRequestedDateTime": "String (timestamp)",
  "policyId": "String",
  "protectionSources": "String",
  "siteId": "String",
  "siteName": "String",
  "siteWebUrl": "String",
  "status": "String"
}
```
