<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheralhealth?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkPeripheralHealth resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents health details for a peripheral device attached to a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| connection | [teamworkConnection](https://learn.microsoft.com/en-us/graph/api/resources/teamworkconnection?view=graph-rest-beta) | The connected state and time since the peripheral device was connected. |
| isOptional | Boolean | `True` if the peripheral is optional. Used for health computation. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| peripheral | [teamworkPeripheral](https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta) | Information about the peripheral device. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkPeripheralHealth",
  "connection": {
    "@odata.type": "microsoft.graph.teamworkConnection"
  },
  "isOptional": "Boolean"
}
```
