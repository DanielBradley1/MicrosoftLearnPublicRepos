<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# depVisionOSEnrollmentProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The enrollmentProfile resource represents a collection of configurations which must be provided pre-enrollment to enable enrolling certain devices whose identities have been pre-staged. Pre-staged device identities are assigned to this type of profile to apply the profile's configurations at enrollment of the corresponding device.

Inherits from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List depVisionOSEnrollmentProfiles](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depvisionosenrollmentprofile-list?view=graph-rest-beta) | [depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta) collection | List properties and relationships of the [depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta) objects. |
| [Get depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depvisionosenrollmentprofile-get?view=graph-rest-beta) | [depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta) | Read properties and relationships of the [depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta) object. |
| [Create depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depvisionosenrollmentprofile-create?view=graph-rest-beta) | [depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta) | Create a new [depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta) object. |
| [Delete depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depvisionosenrollmentprofile-delete?view=graph-rest-beta) | None | Deletes a [depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta). |
| [Update depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-depvisionosenrollmentprofile-update?view=graph-rest-beta) | [depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta) | Update the properties of a [depVisionOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-depvisionosenrollmentprofile?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| displayName | String | Name of the profile Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| description | String | Description of the profile Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| requiresUserAuthentication | Boolean | Indicates if the profile requires user authentication Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| configurationEndpointUrl | String | Configuration endpoint url to use for Enrollment Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| enableAuthenticationViaCompanyPortal | Boolean | Indicates to authenticate with Apple Setup Assistant instead of Company Portal. Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |
| requireCompanyPortalOnSetupAssistantEnrolledDevices | Boolean | Indicates that Company Portal is required on setup assistant enrolled devices Inherited from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.depVisionOSEnrollmentProfile",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "requiresUserAuthentication": true,
  "configurationEndpointUrl": "String",
  "enableAuthenticationViaCompanyPortal": true,
  "requireCompanyPortalOnSetupAssistantEnrolledDevices": true
}
```
