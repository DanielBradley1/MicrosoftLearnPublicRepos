<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkperipheral?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamworkPeripheral resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the details about the peripherals attached to a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name for the peripheral. |
| id | String | Unique identifier for the particular peripheral. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| productId | String | The product ID of the device. Each product from a vendor has its own ID. |
| vendorId | String | The unique identifier for the vendor of the device. Each vendor has a unique ID. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkPeripheral",
  "displayName": "String",
  "id": "String (identifier)",
  "productId": "String",
  "vendorId": "String"
}
```
