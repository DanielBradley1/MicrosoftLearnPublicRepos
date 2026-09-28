<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/controlscore?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# controlScore resource type

Namespace: microsoft.graph

Contains a tenant score and description for an individual control.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| controlCategory | String | Control action category \(Identity, Data, Device, Apps, Infrastructure\). |
| controlName | String | Control unique name. |
| description | String | Description of the control. |
| score | Double | Tenant achieved score for the control \(it varies day by day depending on tenant operations on the control\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "controlCategory": "String",
  "controlName": "String",
  "description": "String",
  "score": "Double"
}
```
