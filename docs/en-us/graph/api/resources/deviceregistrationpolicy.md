<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# deviceRegistrationPolicy resource type

Namespace: microsoft.graph

Represents the policy scope that controls quota restrictions, additional authentication, and authorization policies to register device identities to your organization.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/deviceregistrationpolicy-get?view=graph-rest-1.0) | [deviceRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0) | Read the properties of a [deviceRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/deviceregistrationpolicy-update?view=graph-rest-1.0) | [deviceRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0) | Update the properties of a [deviceRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| azureADJoin | [azureADJoinPolicy](https://learn.microsoft.com/en-us/graph/api/resources/azureadjoinpolicy?view=graph-rest-1.0) | Specifies the authorization policy for controlling registration of new devices using **Microsoft Entra join** within your organization. Required. For more information, see [What is a device identity?](https://learn.microsoft.com/en-us/azure/active-directory/devices/overview). |
| azureADRegistration | [azureADRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/azureadregistrationpolicy?view=graph-rest-1.0) | Specifies the authorization policy for controlling registration of new devices using **Microsoft Entra registered** within your organization. Required. For more information, see [What is a device identity?](https://learn.microsoft.com/en-us/azure/active-directory/devices/overview). |
| description | String | The description of the device registration policy. Always set to `Tenant-wide policy that manages intial provisioning controls using quota restrictions, additional authentication and authorization checks`. Read-only. |
| displayName | String | The name of the device registration policy. Always set to `Device Registration Policy`. Read-only. |
| id | String | The identifier of the device registration policy. Always set to `deviceRegistrationPolicy`. Read-only. |
| localAdminPassword | [localAdminPasswordSettings](https://learn.microsoft.com/en-us/graph/api/resources/localadminpasswordsettings?view=graph-rest-1.0) | Specifies the setting for **Local Admin Password Solution \(LAPS\)** within your organization. |
| multiFactorAuthConfiguration | multiFactorAuthConfiguration | Specifies the authentication policy for a user to complete registration using **Microsoft Entra join** or **Microsoft Entra registered** within your organization. The possible values are: `notRequired`, `required`, `unknownFutureValue`. The default value is `notRequired`. |
| userDeviceQuota | Int32 | Specifies the maximum number of devices that a user can have within your organization before blocking new device registrations. The default value is set to 50. If this property isn't specified during the policy update operation, it's automatically reset to `0` to indicate that users aren't allowed to join any devices. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceRegistrationPolicy",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "userDeviceQuota": "Integer",
  "multiFactorAuthConfiguration": "String",
  "azureADRegistration": {
    "@odata.type": "microsoft.graph.azureADRegistrationPolicy"
  },
  "azureADJoin": {
    "@odata.type": "microsoft.graph.azureADJoinPolicy"
  },
  "localAdminPassword": {
    "@odata.type": "microsoft.graph.localAdminPasswordSettings"
  }
}
```
