<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/backuppolicyreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# backupPolicyReport resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a report that corresponds to a backup policy. This report contains metrics like backup count statistics which shows the number of artifacts in various stages of protection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| backupPolicyId | String | The ID of the backup policy. |
| countStatistics | [backupCountStatistics](https://learn.microsoft.com/en-us/graph/api/resources/backupcountstatistics?view=graph-rest-beta) | The count of artifacts in various protection stages. |
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
