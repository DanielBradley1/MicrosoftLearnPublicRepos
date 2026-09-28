<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# depTvOSEnrollmentProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The depTvOSEnrollmentProfile resource represents an Apple Device Enrollment Program \(DEP\) enrollment profile specific to Apple TV device configuration. This type of profile must be assigned to Apple TV devices before the devices can enroll via DEP. However, This entity type will only be used as a navigation property to fetch the display name of the profile while getting the exitsing depOnboardingSetting entity, it won't support any operations, as the new entity is supported in device configuration\(DCV2\) graph calls

Inherits from [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List depTvOSEnrollmentProfiles](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deptvosenrollmentprofile-list?view=graph-rest-beta) | [depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta) collection | List properties and relationships of the [depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta) objects. |
| [Get depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deptvosenrollmentprofile-get?view=graph-rest-beta) | [depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta) | Read properties and relationships of the [depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta) object. |
| [Create depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deptvosenrollmentprofile-create?view=graph-rest-beta) | [depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta) | Create a new [depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta) object. |
| [Delete depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deptvosenrollmentprofile-delete?view=graph-rest-beta) | None | Deletes a [depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta). |
| [Update depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-deptvosenrollmentprofile-update?view=graph-rest-beta) | [depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta) | Update the properties of a [depTvOSEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-deptvosenrollmentprofile?view=graph-rest-beta) object. |

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
  "@odata.type": "#microsoft.graph.depTvOSEnrollmentProfile",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "requiresUserAuthentication": true,
  "configurationEndpointUrl": "String",
  "enableAuthenticationViaCompanyPortal": true,
  "requireCompanyPortalOnSetupAssistantEnrolledDevices": true
}
```
