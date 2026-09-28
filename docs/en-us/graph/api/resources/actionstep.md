<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/actionstep?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# actionStep resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a single action to take toward completing a [recommendation](https://learn.microsoft.com/en-us/graph/api/resources/recommendation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionUrl | [actionUrl](https://learn.microsoft.com/en-us/graph/api/resources/actionurl?view=graph-rest-beta) | A link to the documentation or Microsoft Entra admin center page that is associated with the action step. |
| stepNumber | Int64 | Indicates the position for this action in the order of the collection of actions to be taken. |
| text | String | Friendly description of the action to take. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.actionStep",
  "stepNumber": "Integer",
  "text": "String",
  "actionUrl": {
    "@odata.type": "microsoft.graph.actionUrl"
  }
}
```
