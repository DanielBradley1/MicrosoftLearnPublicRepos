<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkconfiguredperipheral?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# teamworkConfiguredPeripheral resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about a peripheral device configured for a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isOptional | Boolean | `True` if the current peripheral is optional. If set to `false`, this property is also used as part of the calculation of the health state for the device. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| peripheral | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) | Details about the peripheral devices attached. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkConfiguredPeripheral",
  "isOptional": "Boolean"
}
```
