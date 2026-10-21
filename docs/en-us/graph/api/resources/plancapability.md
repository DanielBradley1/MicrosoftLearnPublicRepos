<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plancapability?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# planCapability resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **capabilities** property of the [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) resource uses this type.

Server-computed, read-only capability flags indicating which optional features are enabled for a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| calendar | Boolean | Indicates whether calendar features are enabled for the plan. |
| customFields | Boolean | Indicates whether custom fields are enabled for the plan. |
| extensions | Boolean | Indicates whether custom extension fields are enabled for the plan. |
| goals | Boolean | Indicates whether goals are enabled for the plan. |
| undo | Boolean | Indicates whether undo is enabled for the plan. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.planCapability",
  "calendar": "Boolean",
  "customFields": "Boolean",
  "extensions": "Boolean",
  "goals": "Boolean",
  "undo": "Boolean"
}
```
