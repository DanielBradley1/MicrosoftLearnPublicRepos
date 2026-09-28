<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/actionurl?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# actionUrl resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The link to the documentation or Microsoft Entra admin center page that provides more information about an [actionStep](https://learn.microsoft.com/en-us/graph/api/resources/actionstep?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Brief title for the page that the links directs to. |
| url | String | The URL to the documentation or Microsoft Entra admin center page. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.actionUrl",
  "displayName": "String",
  "url": "String"
}
```
