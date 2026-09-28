<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsRemoteConnection resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics remote connection entity. The report will be retired on December 31, 2024. You can start using the Cloud PC connection quality report now via [https://learn.microsoft.com/windows-365/enterprise/report-cloud-pc-connection-quality](https://learn.microsoft.com/en-us/windows-365/enterprise/report-cloud-pc-connection-quality).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsRemoteConnections](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsremoteconnection-list?view=graph-rest-beta) | [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsremoteconnection-get?view=graph-rest-beta) | [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsremoteconnection-create.md?view=graph-rest-beta) | [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta) | Create a new [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsremoteconnection-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta). |
| [Update userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsremoteconnection-update.md?view=graph-rest-beta) | [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta) object. |
| [summarizeDeviceRemoteConnection function](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsremoteconnection-summarizedeviceremoteconnection?view=graph-rest-beta) | [userExperienceAnalyticsRemoteConnection](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsremoteconnection?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics remote connection entity. |
| deviceId | String | The id of the device. |
| deviceName | String | The name of the device. |
| model | String | The user experience analytics device model. |
| virtualNetwork | String | The user experience analytics virtual network. |
| manufacturer | String | The user experience analytics manufacturer. |
| deviceCount | Int32 | The count of remote connection. Valid values 0 to 2147483647 |
| cloudPcRoundTripTime | Double | The round tip time of Cloud PC Device. Valid values 0 to 1.79769313486232E+308 |
| cloudPcSignInTime | Double | The sign in time of Cloud PC Device. Valid values 0 to 1.79769313486232E+308 |
| remoteSignInTime | Double | The remote sign in time of Cloud PC Device. Valid values 0 to 1.79769313486232E+308 |
| coreBootTime | Double | The core boot time of Cloud PC Device. Valid values 0 to 1.79769313486232E+308 |
| coreSignInTime | Double | The core sign in time of Cloud PC Device. Valid values 0 to 1.79769313486232E+308 |
| cloudPcFailurePercentage | Double | The sign in failure percentage of Cloud PC Device. Valid values 0 to 100 |
| userPrincipalName | String | The user experience analytics userPrincipalName. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsRemoteConnection",
  "id": "String (identifier)",
  "deviceId": "String",
  "deviceName": "String",
  "model": "String",
  "virtualNetwork": "String",
  "manufacturer": "String",
  "deviceCount": 1024,
  "cloudPcRoundTripTime": "4.2",
  "cloudPcSignInTime": "4.2",
  "remoteSignInTime": "4.2",
  "coreBootTime": "4.2",
  "coreSignInTime": "4.2",
  "cloudPcFailurePercentage": "4.2",
  "userPrincipalName": "String"
}
```
