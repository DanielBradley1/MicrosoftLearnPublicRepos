<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fileaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# fileAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-beta) that targets files returned by a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) hunting query. The action uses file hash columns from the query output to identify the files.

Inherits from [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceGroupNames | String collection | Names of the device groups where the file action applies. |
| sha1Column | String | Name of the hunting-query result column that contains the SHA-1 hash of the targeted file. |
| sha256Column | String | Name of the hunting-query result column that contains the SHA-256 hash of the targeted file. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.fileAction",
  "deviceGroupNames": [
    "String"
  ],
  "sha1Column": "String",
  "sha256Column": "String"
}
```
