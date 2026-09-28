<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-migratesensorsresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# migrateSensorsResult resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the result of a sensor migration operation in Microsoft Defender for Identity. Contains the lists of sensor IDs that were successfully migrated and those that failed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedMigrationSensorIds | String collection | The collection of sensor IDs that failed to migrate. |
| successfulMigrationSensorIds | String collection | The collection of sensor IDs that were successfully migrated. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.migrateSensorsResult",
  "successfulMigrationSensorIds": [
    "String"
  ],
  "failedMigrationSensorIds": [
    "String"
  ]
}
```
