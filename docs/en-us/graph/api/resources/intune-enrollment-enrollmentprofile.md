<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# enrollmentProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The enrollmentProfile resource represents a collection of configurations which must be provided pre-enrollment to enable enrolling certain devices whose identities have been pre-staged. Pre-staged device identities are assigned to this type of profile to apply the profile's configurations at enrollment of the corresponding device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List enrollmentProfiles](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-enrollmentprofile-list?view=graph-rest-beta) | [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) collection | List properties and relationships of the [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) objects. |
| [Get enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-enrollmentprofile-get?view=graph-rest-beta) | [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) | Read properties and relationships of the [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) object. |
| [Create enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-enrollmentprofile-create?view=graph-rest-beta) | [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) | Create a new [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) object. |
| [Delete enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-enrollmentprofile-delete?view=graph-rest-beta) | None | Deletes a [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta). |
| [Update enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-enrollmentprofile-update?view=graph-rest-beta) | [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) | Update the properties of a [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) object. |
| [setDefaultProfile action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-enrollmentprofile-setdefaultprofile?view=graph-rest-beta) | None |  |
| [exportMobileConfig function](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-enrollmentprofile-exportmobileconfig?view=graph-rest-beta) | String | Exports the mobile configuration |
| [updateDeviceProfileAssignment action](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-enrollmentprofile-updatedeviceprofileassignment?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object |
| displayName | String | Name of the profile |
| description | String | Description of the profile |
| requiresUserAuthentication | Boolean | Indicates if the profile requires user authentication |
| configurationEndpointUrl | String | Configuration endpoint url to use for Enrollment |
| enableAuthenticationViaCompanyPortal | Boolean | Indicates to authenticate with Apple Setup Assistant instead of Company Portal. |
| requireCompanyPortalOnSetupAssistantEnrolledDevices | Boolean | Indicates that Company Portal is required on setup assistant enrolled devices |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.enrollmentProfile",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "requiresUserAuthentication": true,
  "configurationEndpointUrl": "String",
  "enableAuthenticationViaCompanyPortal": true,
  "requireCompanyPortalOnSetupAssistantEnrolledDevices": true
}
```
