<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-itembody?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# itemBody resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a container for holding content and its type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The content of the item. |
| contentType | microsoft.graph.windowsUpdates.bodyType | The type of the content indicated by the enum value of **bodyType**. The possible values are: `text`, `html`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.itemBody",
  "content": "String",
  "contentType": "String"
}
```
