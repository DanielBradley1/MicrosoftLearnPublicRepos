<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usageright?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# usageRight resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A usage right represents a license that a user or device has for either third party software built on Power Apps or for device-based subscriptions \(device only\).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List user usage rights](https://learn.microsoft.com/en-us/graph/api/user-list-usagerights?view=graph-rest-beta) | [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/usageright?view=graph-rest-beta) collection | Get the list of usage rights for a user. |
| [List device usage rights](https://learn.microsoft.com/en-us/graph/api/device-list-usagerights?view=graph-rest-beta) | [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/usageright?view=graph-rest-beta) collection | Get the list of usage rights for a device. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| catalogId | String | Product id corresponding to the usage right. |
| id | String | The id of the usage right. |
| serviceIdentifier | String | Identifier of the service corresponding to the usage right. |
| state | usageRightState | The state of the usage right. The possible values are: `active`, `inactive`, `warning`, `suspended`. |

### usageRightState values

| Member | Description |
| :--- | :--- |
| active | Indicates that the usage right is active and can be used for provisioning benefits. |
| inactive | Indicates that the usage right isn't active and can't be used for provisioning benefits. |
| warning | Indicates that the usage right is in grace likely due to payment violation. This state can be used to either remind of pending payment or offer a degraded experience. |
| suspended | Indicates that the usage right is suspended likely due to Payment violation |
| unknownFutureValue | Sentinel value to indicate future values. |

> **Note:** Only the active and warning states represent a usable benefit. All other states should be treated as not resulting in a usable benefit.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.usageRight",
  "id": "String (identifier)",
  "catalogId": "String",
  "serviceIdentifier": "String",
  "state": "String"
}
```
