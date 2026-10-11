<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/protectionunitdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-10 -->

# protectionUnitDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed count information about protection units associated with a backup policy, including the number of units requested to be added or removed, successfully added or removed, and failed operations.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| addedCount | Int32 | The number of protection units that were successfully added to the backup policy. |
| backupConfigurationType | String | The type of backup configuration applied to the protection units. |
| failedCount | Int32 | The number of protection unit operations that failed during processing. |
| removedCount | Int32 | The number of protection units that were successfully removed from the backup policy. |
| requestedToAddCount | Int32 | The number of protection units that were requested to be added to the backup policy. |
| requestedToRemoveCount | Int32 | The number of protection units that were requested to be removed from the backup policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.protectionUnitDetails",
  "requestedToAddCount": "Integer",
  "requestedToRemoveCount": "Integer",
  "addedCount": "Integer",
  "removedCount": "Integer",
  "failedCount": "Integer",
  "backupConfigurationType": "String"
}
```
