<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-submissiondetectedfile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# submissionDetectedFile resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the information of a detected file in a threat submission.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| fileHash | String | The file hash. |
| fileName | String | The file name. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.submissionDetectedFile",
  "fileName": "String",
  "fileHash": "String"
}
```
