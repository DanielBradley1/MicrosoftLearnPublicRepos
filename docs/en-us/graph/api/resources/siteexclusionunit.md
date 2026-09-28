<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/siteexclusionunit?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# siteExclusionUnit resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a SharePoint site that is excluded from a [SharePoint protection policy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-beta) configured for full workload backup.

Inherits from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/sharepointprotectionpolicy-list-siteexclusionunits?view=graph-rest-beta) | [siteExclusionUnit](https://learn.microsoft.com/en-us/graph/api/resources/siteexclusionunit?view=graph-rest-beta) collection | Get a list of [site exclusion units](https://learn.microsoft.com/en-us/graph/api/resources/siteexclusionunit?view=graph-rest-beta) associated with a [SharePoint protection policy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-beta). |
| [Get](https://learn.microsoft.com/en-us/graph/api/siteexclusionunit-get?view=graph-rest-beta) | [siteExclusionUnit](https://learn.microsoft.com/en-us/graph/api/resources/siteexclusionunit?view=graph-rest-beta) | Get a [site exclusion unit](https://learn.microsoft.com/en-us/graph/api/resources/siteexclusionunit?view=graph-rest-beta) associated with a [SharePoint protection policy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the person who created the exclusion unit. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the exclusion unit was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | Contains error details if the exclusion unit is in a failed state. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| id | String | The unique identifier of the exclusion unit. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the person who last modified the exclusion unit. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the exclusion unit was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| policyId | String | The unique identifier of the protection policy that contains this exclusion unit. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| siteId | String | The unique identifier of the SharePoint site. |
| siteName | String | The display name of the SharePoint site. |
| siteWebUrl | String | The URL of the SharePoint site. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.siteExclusionUnit",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "policyId": "String",
  "siteId": "String",
  "siteName": "String",
  "siteWebUrl": "String"
}
```
