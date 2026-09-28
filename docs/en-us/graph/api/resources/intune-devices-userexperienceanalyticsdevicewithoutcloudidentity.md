<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsDeviceWithoutCloudIdentity resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics Device without Cloud Identity.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsDeviceWithoutCloudIdentities](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity-list?view=graph-rest-beta) | [userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity-get?view=graph-rest-beta) | [userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity-create.md?view=graph-rest-beta) | [userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity?view=graph-rest-beta) | Create a new [userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity?view=graph-rest-beta). |
| [Update userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity-update.md?view=graph-rest-beta) | [userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsDeviceWithoutCloudIdentity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicewithoutcloudidentity?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics tenant attach device. |
| deviceName | String | The tenant attach device's name. |
| azureAdDeviceId | String | Azure Active Directory Device Id |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsDeviceWithoutCloudIdentity",
  "id": "String (identifier)",
  "deviceName": "String",
  "azureAdDeviceId": "String"
}
```
