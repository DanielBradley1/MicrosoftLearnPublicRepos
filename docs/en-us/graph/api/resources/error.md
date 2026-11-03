<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/error?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-20 -->

# Error resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details of an error with a message and error code.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The error code |
| message | String | The message for the error |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.error",
  "code": "String",
  "message": "String"
}
```
