<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-stopandquarantinefileaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# stopAndQuarantineFileAction resource type

Namespace: microsoft.graph.security

Represents an [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-1.0) that stops and quarantines a file on a device returned by a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) hunting query. The action uses device ID and SHA-1 columns from the query output to identify where to stop and quarantine the file.

Inherits from [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceIdColumn | String | Name of the hunting-query result column that contains the device ID for the device where the file was observed. |
| sha1Column | String | Name of the hunting-query result column that contains the SHA-1 hash of the file to stop and quarantine. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.stopAndQuarantineFileAction",
  "deviceIdColumn": "String",
  "sha1Column": "String"
}
```
