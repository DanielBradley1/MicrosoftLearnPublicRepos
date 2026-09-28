<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsFeatureUpdateProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Feature Update Profile

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsFeatureUpdateProfiles](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofile-list?view=graph-rest-beta) | [windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile?view=graph-rest-beta) collection | List properties and relationships of the [windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile?view=graph-rest-beta) objects. |
| [Get windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofile-get?view=graph-rest-beta) | [windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile?view=graph-rest-beta) | Read properties and relationships of the [windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile?view=graph-rest-beta) object. |
| [Create windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofile-create?view=graph-rest-beta) | [windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile?view=graph-rest-beta) | Create a new [windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile?view=graph-rest-beta) object. |
| [Delete windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofile-delete?view=graph-rest-beta) | None | Deletes a [windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile?view=graph-rest-beta). |
| [Update windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofile-update?view=graph-rest-beta) | [windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile?view=graph-rest-beta) | Update the properties of a [windowsFeatureUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofile?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdateprofile-assign?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The Identifier of the entity. |
| displayName | String | The display name of the profile. |
| description | String | The description of the profile which is specified by the user. |
| featureUpdateVersion | String | The feature update version that will be deployed to the devices targeted by this profile. The version could be any supported version for example 1709, 1803 or 1809 and so on. |
| rolloutSettings | [windowsUpdateRolloutSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdaterolloutsettings?view=graph-rest-beta) | The windows update rollout settings, including offer start date time, offer end date time, and days between each set of offers. |
| createdDateTime | DateTimeOffset | The date time that the profile was created. |
| lastModifiedDateTime | DateTimeOffset | The date time that the profile was last modified. |
| roleScopeTagIds | String collection | List of Scope Tags for this Feature Update entity. |
| deployableContentDisplayName | String | Friendly display name of the quality update profile deployable content |
| endOfSupportDate | DateTimeOffset | The last supported date for a feature update |
| installLatestWindows10OnWindows11IneligibleDevice | Boolean | If true, the latest Microsoft Windows 10 update will be installed on devices ineligible for Microsoft Windows 11 |
| installFeatureUpdatesOptional | Boolean | If true, the Windows 11 update will become optional |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [windowsFeatureUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdateprofileassignment?view=graph-rest-beta) collection | The list of group assignments of the profile. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsFeatureUpdateProfile",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "featureUpdateVersion": "String",
  "rolloutSettings": {
    "@odata.type": "microsoft.graph.windowsUpdateRolloutSettings",
    "offerStartDateTimeInUTC": "String (timestamp)",
    "offerEndDateTimeInUTC": "String (timestamp)",
    "offerIntervalInDays": 1024
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "deployableContentDisplayName": "String",
  "endOfSupportDate": "String (timestamp)",
  "installLatestWindows10OnWindows11IneligibleDevice": true,
  "installFeatureUpdatesOptional": true
}
```
