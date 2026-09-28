<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# endpointPrivilegeManagementProvisioningStatus resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Endpoint privilege management \(EPM\) tenant provisioning status contains tenant level license and onboarding state information.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get endpointPrivilegeManagementProvisioningStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus-get?view=graph-rest-beta) | [endpointPrivilegeManagementProvisioningStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus?view=graph-rest-beta) | Read properties and relationships of the [endpointPrivilegeManagementProvisioningStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus?view=graph-rest-beta) object. |
| [Update endpointPrivilegeManagementProvisioningStatus](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus-update?view=graph-rest-beta) | [endpointPrivilegeManagementProvisioningStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus?view=graph-rest-beta) | Update the properties of a [endpointPrivilegeManagementProvisioningStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | A unique identifier represents Intune Account identifier. |
| licenseType | [licenseType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-licensetype?view=graph-rest-beta) | Indicates whether tenant has a valid Intune Endpoint Privilege Management license. Possible value are : 0 - notPaid, 1 - paid, 2 - trial. See LicenseType enum for more details. Default notPaid. Possible values are: `notPaid`, `paid`, `trial`, `unknownFutureValue`. |
| onboardedToMicrosoftManagedPlatform | Boolean | Indicates whether tenant is onboarded to Microsoft Managed Platform - Cloud \(MMPC\). When set to true, implies tenant is onboarded and when set to false, implies tenant is not onboarded. Default set to false. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.endpointPrivilegeManagementProvisioningStatus",
  "id": "String (identifier)",
  "licenseType": "String",
  "onboardedToMicrosoftManagedPlatform": true
}
```
