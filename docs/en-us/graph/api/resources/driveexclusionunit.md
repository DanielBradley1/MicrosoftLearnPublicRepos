<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driveexclusionunit?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# driveExclusionUnit resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a OneDrive drive that is excluded from a [OneDrive for work or school protection policy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-beta) configured for full workload backup.

Inherits from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessprotectionpolicy-list-driveexclusionunits?view=graph-rest-beta) | [driveExclusionUnit](https://learn.microsoft.com/en-us/graph/api/resources/driveexclusionunit?view=graph-rest-beta) collection | Get a list of [drive exclusion units](https://learn.microsoft.com/en-us/graph/api/resources/driveexclusionunit?view=graph-rest-beta) associated with a [OneDrive for work or school protection policy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-beta). |
| [Get](https://learn.microsoft.com/en-us/graph/api/driveexclusionunit-get?view=graph-rest-beta) | [driveExclusionUnit](https://learn.microsoft.com/en-us/graph/api/resources/driveexclusionunit?view=graph-rest-beta) | Get a [drive exclusion unit](https://learn.microsoft.com/en-us/graph/api/resources/driveexclusionunit?view=graph-rest-beta) associated with a [OneDrive for work or school protection policy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the person who created the exclusion unit. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the exclusion unit was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| directoryObjectId | String | The unique identifier of the directory object \(user\) associated with the drive. |
| displayName | String | The display name of the user associated with the drive. |
| email | String | The email address of the user associated with the drive. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | Contains error details if the exclusion unit is in a failed state. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| id | String | The unique identifier of the exclusion unit. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the person who last modified the exclusion unit. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the exclusion unit was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |
| policyId | String | The unique identifier of the protection policy that contains this exclusion unit. Inherited from [exclusionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/exclusionunitbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driveExclusionUnit",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "directoryObjectId": "String",
  "displayName": "String",
  "email": "String",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "policyId": "String"
}
```
