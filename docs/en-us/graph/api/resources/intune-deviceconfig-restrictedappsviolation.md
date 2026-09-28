<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# restrictedAppsViolation resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Violation of restricted apps configuration profile per device per user

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List restrictedAppsViolations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-restrictedappsviolation-list?view=graph-rest-beta) | [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta) collection | List properties and relationships of the [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta) objects. |
| [Get restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-restrictedappsviolation-get?view=graph-rest-beta) | [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta) | Read properties and relationships of the [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta) object. |
| [Create restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-restrictedappsviolation-create?view=graph-rest-beta) | [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta) | Create a new [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta) object. |
| [Delete restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-restrictedappsviolation-delete?view=graph-rest-beta) | None | Deletes a [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta). |
| [Update restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-restrictedappsviolation-update?view=graph-rest-beta) | [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta) | Update the properties of a [restrictedAppsViolation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsviolation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the object. Composed from accountId, deviceId, policyId and userId |
| userId | String | User unique identifier, must be Guid |
| userName | String | User name |
| managedDeviceId | String | Managed device unique identifier, must be Guid |
| deviceName | String | Device name |
| deviceConfigurationId | String | Device configuration profile unique identifier, must be Guid |
| deviceConfigurationName | String | Device configuration profile name |
| platformType | [policyPlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-policyplatformtype?view=graph-rest-beta) | Platform type. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `windows10XProfile`, `androidAOSP`, `linux`, `all`. |
| restrictedAppsState | [restrictedAppsState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-restrictedappsstate?view=graph-rest-beta) | Restricted apps state. Possible values are: `prohibitedApps`, `notApprovedApps`. |
| restrictedApps | [managedDeviceReportedApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicereportedapp?view=graph-rest-beta) collection | List of violated restricted apps |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.restrictedAppsViolation",
  "id": "String (identifier)",
  "userId": "String",
  "userName": "String",
  "managedDeviceId": "String",
  "deviceName": "String",
  "deviceConfigurationId": "String",
  "deviceConfigurationName": "String",
  "platformType": "String",
  "restrictedAppsState": "String",
  "restrictedApps": [
    {
      "@odata.type": "microsoft.graph.managedDeviceReportedApp",
      "appId": "String"
    }
  ]
}
```
