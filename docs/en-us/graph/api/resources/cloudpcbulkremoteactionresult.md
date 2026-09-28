<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkremoteactionresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# cloudPcBulkRemoteActionResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Cloud PC-specified bulk remote action result.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedDeviceIds | String collection | A list of all the Intune managed device IDs that completed the bulk action with a failure. |
| notFoundDeviceIds | String collection | A list of all the Intune managed device IDs that were not found when the bulk action was attempted. |
| notSupportedDeviceIds | String collection | A list of all the Intune managed device IDs that were identified as unsupported for the bulk action. |
| successfulDeviceIds | String collection | A list of all the Intune managed device IDs that completed the bulk action successfully. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcBulkRemoteActionResult",
  "failedDeviceIds": [
    "String"
  ],
  "notFoundDeviceIds": [
    "String"
  ],
  "notSupportedDeviceIds": [
    "String"
  ],
  "successfulDeviceIds": [
    "String"
  ]
}
```
