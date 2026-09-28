<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-conditionalaccesssettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# conditionalAccessSettings resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Conditional access settings define how you can restore users source IP and how you can use compliant network validation. Source IP restoration preserves your original user IP context for all Microsoft Entra ID and Microsoft 365 traffic, and compliant network validation ensures the user is connecting from a verified network.

For more information about conditional access settings, see [Universal Conditional Access through Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-universal-conditional-access) and [Source IP restoration](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-universal-tenant-restrictions).

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-conditionalaccesssettings-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.conditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-conditionalaccesssettings?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.conditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-conditionalaccesssettings?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-conditionalaccesssettings-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.conditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-conditionalaccesssettings?view=graph-rest-beta) | Update the properties of a [microsoft.graph.networkaccess.conditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-conditionalaccesssettings?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| signalingStatus | microsoft.graph.networkaccess.status | When SignalingStatus is enabled, the Conditional Access policy includes zero trust network access information. The possible values are: `enabled`, `disabled`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.conditionalAccessSettings",
  "id": "String (identifier)",
  "signalingStatus": "String"
}
```
