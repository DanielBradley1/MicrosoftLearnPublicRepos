<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsQualityUpdateProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Quality Update Profile

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsQualityUpdateProfiles](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdateprofile-list?view=graph-rest-beta) | [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) collection | List properties and relationships of the [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) objects. |
| [Get windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdateprofile-get?view=graph-rest-beta) | [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) | Read properties and relationships of the [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) object. |
| [Create windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdateprofile-create?view=graph-rest-beta) | [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) | Create a new [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) object. |
| [Delete windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdateprofile-delete?view=graph-rest-beta) | None | Deletes a [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta). |
| [Update windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdateprofile-update?view=graph-rest-beta) | [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) | Update the properties of a [windowsQualityUpdateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofile?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdateprofile-assign?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The Intune policy id. |
| displayName | String | The display name for the profile. |
| description | String | The description of the profile which is specified by the user. |
| expeditedUpdateSettings | [expeditedWindowsQualityUpdateSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-expeditedwindowsqualityupdatesettings?view=graph-rest-beta) | Expedited update settings. |
| createdDateTime | DateTimeOffset | The date time that the profile was created. |
| lastModifiedDateTime | DateTimeOffset | The date time that the profile was last modified. |
| roleScopeTagIds | String collection | List of Scope Tags for this Quality Update entity. |
| releaseDateDisplayName | String | Friendly release date to display for a Quality Update release |
| deployableContentDisplayName | String | Friendly display name of the quality update profile deployable content |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [windowsQualityUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateprofileassignment?view=graph-rest-beta) collection | The list of group assignments of the profile. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsQualityUpdateProfile",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "expeditedUpdateSettings": {
    "@odata.type": "microsoft.graph.expeditedWindowsQualityUpdateSettings",
    "qualityUpdateRelease": "String",
    "daysUntilForcedReboot": 1024
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "releaseDateDisplayName": "String",
  "deployableContentDisplayName": "String"
}
```
