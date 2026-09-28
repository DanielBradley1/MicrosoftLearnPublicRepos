<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/dynamics-shipmentmethods?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# shipmentMethod resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a method of shipment in Dynamics 365 Business Central, such as UPS, Fedex, and DHL.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get shipment methods](https://learn.microsoft.com/en-us/graph/api/dynamics-shipmentmethods-get?view=graph-rest-beta) | shipmentMethod | Get a shipment method. |
| [Create shipment methods](https://learn.microsoft.com/en-us/graph/api/dynamics-create-shipmentmethods?view=graph-rest-beta) | shipmentMethod | Create a shipment method. |
| [Update shipment methods](https://learn.microsoft.com/en-us/graph/api/dynamics-shipmentmethods-update?view=graph-rest-beta) | shipmentMethod | Update a shipment method. |
| [Delete shipment methods](https://learn.microsoft.com/en-us/graph/api/dynamics-shipmentmethods-delete?view=graph-rest-beta) | None | Delete a shipment method. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The shipment method code. |
| displayName | String | The display name for the shipment method. |
| id | String | The unique identifier of the **shipmentMethod**. Noneditable. |
| lastModifiedDateTime | Datetime | The date and time when the shipment method was last modified. Read-Only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "code": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "Datetime"
}
```
