<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/backuppolicyreport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# backupPolicyReport resource type

Namespace: microsoft.graph

Represents a report that corresponds to a backup policy. This report contains metrics like backup count statistics that show the number of artifacts in various stages of protection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| backupPolicyId | String | The ID of the backup policy. |
| countStatistics | [backupCountStatistics](https://learn.microsoft.com/en-us/graph/api/resources/backupcountstatistics?view=graph-rest-1.0) | The count of artifacts in various protection stages. |
| displayName | String | The display name of the backup policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.backupPolicyReport",
  "backupPolicyId": "String",
  "countStatistics": {"@odata.type": "microsoft.graph.backupCountStatistics"},
  "displayName": "String"
}
```
