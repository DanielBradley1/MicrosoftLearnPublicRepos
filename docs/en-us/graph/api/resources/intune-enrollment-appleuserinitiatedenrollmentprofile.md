<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# appleUserInitiatedEnrollmentProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The enrollmentProfile resource represents a collection of configurations which must be provided pre-enrollment to enable enrolling certain devices whose identities have been pre-staged. Pre-staged device identities are assigned to this type of profile to apply the profile's configurations at enrollment of the corresponding device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List appleUserInitiatedEnrollmentProfiles](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleuserinitiatedenrollmentprofile-list?view=graph-rest-beta) | [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta) collection | List properties and relationships of the [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta) objects. |
| [Get appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleuserinitiatedenrollmentprofile-get?view=graph-rest-beta) | [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta) | Read properties and relationships of the [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta) object. |
| [Create appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleuserinitiatedenrollmentprofile-create?view=graph-rest-beta) | [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta) | Create a new [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta) object. |
| [Delete appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleuserinitiatedenrollmentprofile-delete?view=graph-rest-beta) | None | Deletes a [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta). |
| [Update appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleuserinitiatedenrollmentprofile-update?view=graph-rest-beta) | [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta) | Update the properties of a [appleUserInitiatedEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmentprofile?view=graph-rest-beta) object. |
| [setPriority action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-appleuserinitiatedenrollmentprofile-setpriority?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultEnrollmentType | [appleUserInitiatedEnrollmentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleuserinitiatedenrollmenttype?view=graph-rest-beta) | The default profile enrollment type. Possible values are: `unknown`, `device`, `user`, `accountDrivenUserEnrollment`, `webDeviceEnrollment`, `unknownFutureValue`. |
| availableEnrollmentTypeOptions | [appleOwnerTypeEnrollmentType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleownertypeenrollmenttype?view=graph-rest-beta) collection | List of available enrollment type options |
| id | String | The GUID for the object |
| displayName | String | Name of the profile |
| description | String | Description of the profile |
| priority | Int32 | Priority, 0 is highest |
| platform | [devicePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deviceplatformtype?view=graph-rest-beta) | The platform of the Device. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidAOSP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`, `windowsMobileApplicationManagement`. |
| createdDateTime | DateTimeOffset | Profile creation time |
| lastModifiedDateTime | DateTimeOffset | Profile last modified time |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [appleEnrollmentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-appleenrollmentprofileassignment?view=graph-rest-beta) collection | The list of assignments for this profile. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.appleUserInitiatedEnrollmentProfile",
  "defaultEnrollmentType": "String",
  "availableEnrollmentTypeOptions": [
    {
      "@odata.type": "microsoft.graph.appleOwnerTypeEnrollmentType",
      "ownerType": "String",
      "enrollmentType": "String"
    }
  ],
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "priority": 1024,
  "platform": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
