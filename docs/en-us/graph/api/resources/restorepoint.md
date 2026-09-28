<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# restorePoint resource type

Namespace: microsoft.graph

Represents the date and time when an [artifact](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactbase?view=graph-rest-1.0) is protected by a [protectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-1.0) and can be restored.

The following limitations apply to this API:

- When sites or mailboxes are added to a backup policy, it might take up to 15 minutes per 1,000 sites or mailboxes for restore points to become available.
- Although OneDrive account and mailbox backups of deleted users are maintained and restorable after the user’s Microsoft Entra ID is deleted, the user is displayed as an empty user in results.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-restorepoints?view=graph-rest-1.0) | [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) collection | Get a list of [restorePoint](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0) objects and their properties. |
| [Search](https://learn.microsoft.com/en-us/graph/api/restorepoint-search?view=graph-rest-1.0) | [restorePointSearchResponse](https://learn.microsoft.com/en-us/graph/api/resources/restorepointsearchresponse?view=graph-rest-1.0) | Search for the restore points associated with a [protectionUnit](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of the restore point. |
| protectionDateTime | DateTimeOffset | Date time when the restore point was created. |
| expirationDateTime | DateTimeOffset | Expiration date time of the restore point. |
| tags | [restorePointTags](https://learn.microsoft.com/en-us/graph/api/resources/restorepoint?view=graph-rest-1.0#restorepointtags-values) | The type of the restore point. The possible values are: `none`, `fastRestore`, `unknownFutureValue`. |

### restorePointTags values

| Member | Description |
| :--- | :--- |
| none | No tag. |
| fastRestore | Get a fast restore point. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| protectionUnit | [protectionUnitBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionunitbase?view=graph-rest-1.0) | The site, drive, or mailbox units that are protected under a protection policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restorePoint",
  "id": "String (identifier)",
  "protectionDateTime": "String (timestamp)",
  "expirationDateTime": "String (timestamp)",
  "tags": "String"
}
```
