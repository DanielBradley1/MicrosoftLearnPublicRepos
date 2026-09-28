<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/labelactionbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-16 -->

# labelActionBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Abstract base type for actions associated with a sensitivity label, like applying encryption or content markings.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the action \(for example, "Encrypt", "AddHeader"\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type. An abstract type that isn't instantiated. Derived types specify the concrete action properties.

```json
{
  "@odata.type": "#microsoft.graph.labelActionBase",
  "name": "String",
  "isEnabled": "Boolean"
}
```
