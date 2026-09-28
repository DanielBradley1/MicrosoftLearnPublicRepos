<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recommendationtag?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# recommendationTag resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user-defined free-form label applied to a Microsoft Entra ID [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta) or [impactedResource](https://learn.microsoft.com/en-us/graph/api/resources/impactedresource?view=graph-rest-beta). Tags help you organize, group, and filter recommendations and impacted resources in the Microsoft Entra admin center.

Tags aren't directly writable through PATCH. Create a tag by using the [addTag](https://learn.microsoft.com/en-us/graph/api/recommendation-addtag?view=graph-rest-beta) action on a recommendation or the [addTag](https://learn.microsoft.com/en-us/graph/api/impactedresource-addtag?view=graph-rest-beta) action on an impacted resource, and remove a tag by using the corresponding [removeTag](https://learn.microsoft.com/en-us/graph/api/recommendation-removetag?view=graph-rest-beta) actions.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The free-form label text. All characters and Unicode \(all languages\) are supported. |
| id | String | The unique identifier of the tag. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.recommendationTag",
  "id": "String (identifier)",
  "displayName": "String"
}
```
