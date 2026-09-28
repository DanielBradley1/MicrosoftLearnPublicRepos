<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeonpremisespolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementExchangeOnPremisesPolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity which represents the Exchange OnPremises policy configured for a tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceManagementExchangeOnPremisesPolicy](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementexchangeonpremisespolicy-get?view=graph-rest-beta) | [deviceManagementExchangeOnPremisesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeonpremisespolicy?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementExchangeOnPremisesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeonpremisespolicy?view=graph-rest-beta) object. |
| [Update deviceManagementExchangeOnPremisesPolicy](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementexchangeonpremisespolicy-update?view=graph-rest-beta) | [deviceManagementExchangeOnPremisesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeonpremisespolicy?view=graph-rest-beta) | Update the properties of a [deviceManagementExchangeOnPremisesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeonpremisespolicy?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| notificationContent | Binary | Notification text that will be sent to users quarantined by this policy. This is UTF8 encoded byte array HTML. |
| defaultAccessLevel | [deviceManagementExchangeAccessLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeaccesslevel?view=graph-rest-beta) | Default access state in Exchange. This rule applies globally to the entire Exchange organization. Possible values are: `none`, `allow`, `block`, `quarantine`. |
| accessRules | [deviceManagementExchangeAccessRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeaccessrule?view=graph-rest-beta) collection | The list of device access rules in Exchange. The access rules apply globally to the entire Exchange organization |
| knownDeviceClasses | [deviceManagementExchangeDeviceClass](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangedeviceclass?view=graph-rest-beta) collection | The list of device classes known to Exchange |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| conditionalAccessSettings | [onPremisesConditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-onpremisesconditionalaccesssettings?view=graph-rest-beta) | The Exchange on premises conditional access settings. On premises conditional access will require devices to be both enrolled and compliant for mail access |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementExchangeOnPremisesPolicy",
  "id": "String (identifier)",
  "notificationContent": "binary",
  "defaultAccessLevel": "String",
  "accessRules": [
    {
      "@odata.type": "microsoft.graph.deviceManagementExchangeAccessRule",
      "deviceClass": {
        "@odata.type": "microsoft.graph.deviceManagementExchangeDeviceClass",
        "name": "String",
        "type": "String"
      },
      "accessLevel": "String"
    }
  ],
  "knownDeviceClasses": [
    {
      "@odata.type": "microsoft.graph.deviceManagementExchangeDeviceClass",
      "name": "String",
      "type": "String"
    }
  ]
}
```
