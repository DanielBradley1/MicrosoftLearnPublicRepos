<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/standardwebpart?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# standardWebPart resource type

Namespace: microsoft.graph

Represents a standard web part instance on a SharePoint page.

Inherits from [webPart](https://learn.microsoft.com/en-us/graph/api/resources/webpart?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| containerTextWebPartId | string | The instance identifier of the container text webPart. It only works for inline standard webPart in rich text webParts. |
| data | [webPartData](https://learn.microsoft.com/en-us/graph/api/resources/webpartdata?view=graph-rest-1.0) | Data of the webPart. |
| id | String | Instance identifier of the webPart. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| webPartType | String | A Guid that indicates the webPart type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.standardWebPart",
  "containerTextWebPartId": "String",
  "id": "String (identifier)",
  "webPartType": "String",
  "data": {
    "@odata.type": "microsoft.graph.webPartData"
  }
}
```
