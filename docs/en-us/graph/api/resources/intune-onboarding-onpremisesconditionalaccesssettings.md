<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-onpremisesconditionalaccesssettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# onPremisesConditionalAccessSettings resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity which represents the Exchange OnPremises Conditional Access Settings for a tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get onPremisesConditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-onpremisesconditionalaccesssettings-get?view=graph-rest-1.0) | [onPremisesConditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-onpremisesconditionalaccesssettings?view=graph-rest-1.0) | Read properties and relationships of the [onPremisesConditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-onpremisesconditionalaccesssettings?view=graph-rest-1.0) object. |
| [Update onPremisesConditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-onpremisesconditionalaccesssettings-update?view=graph-rest-1.0) | [onPremisesConditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-onpremisesconditionalaccesssettings?view=graph-rest-1.0) | Update the properties of a [onPremisesConditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-onpremisesconditionalaccesssettings?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| enabled | Boolean | Indicates if on premises conditional access is enabled for this organization |
| includedGroups | Guid collection | User groups that will be targeted by on premises conditional access. All users in these groups will be required to have mobile device managed and compliant for mail access. |
| excludedGroups | Guid collection | User groups that will be exempt by on premises conditional access. All users in these groups will be exempt from the conditional access policy. |
| overrideDefaultRule | Boolean | Override the default access rule when allowing a device to ensure access is granted. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.onPremisesConditionalAccessSettings",
  "id": "String (identifier)",
  "enabled": true,
  "includedGroups": [
    "Guid"
  ],
  "excludedGroups": [
    "Guid"
  ],
  "overrideDefaultRule": true
}
```
