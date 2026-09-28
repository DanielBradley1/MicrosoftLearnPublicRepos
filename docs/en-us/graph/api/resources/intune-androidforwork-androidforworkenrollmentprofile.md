<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidForWorkEnrollmentProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Enrollment Profile used to enroll COSU devices using Google's Cloud Management.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidForWorkEnrollmentProfiles](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkenrollmentprofile-list?view=graph-rest-beta) | [androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile?view=graph-rest-beta) collection | List properties and relationships of the [androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile?view=graph-rest-beta) objects. |
| [Get androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkenrollmentprofile-get?view=graph-rest-beta) | [androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile?view=graph-rest-beta) | Read properties and relationships of the [androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile?view=graph-rest-beta) object. |
| [Create androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkenrollmentprofile-create?view=graph-rest-beta) | [androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile?view=graph-rest-beta) | Create a new [androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile?view=graph-rest-beta) object. |
| [Delete androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkenrollmentprofile-delete?view=graph-rest-beta) | None | Deletes a [androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile?view=graph-rest-beta). |
| [Update androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkenrollmentprofile-update?view=graph-rest-beta) | [androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile?view=graph-rest-beta) | Update the properties of a [androidForWorkEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkenrollmentprofile?view=graph-rest-beta) object. |
| [revokeToken action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkenrollmentprofile-revoketoken?view=graph-rest-beta) | None |  |
| [createToken action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkenrollmentprofile-createtoken?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountId | String | Tenant GUID the enrollment profile belongs to. |
| id | String | Unique GUID for the enrollment profile. |
| displayName | String | Display name for the enrollment profile. |
| description | String | Description for the enrollment profile. |
| createdDateTime | DateTimeOffset | Date time the enrollment profile was created. |
| lastModifiedDateTime | DateTimeOffset | Date time the enrollment profile was last modified. |
| tokenValue | String | Value of the most recently created token for this enrollment profile. |
| tokenExpirationDateTime | DateTimeOffset | Date time the most recently created token will expire. |
| enrolledDeviceCount | Int32 | Total number of Android devices that have enrolled using this enrollment profile. |
| qrCodeContent | String | String used to generate a QR code for the token. |
| qrCodeImage | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-beta) | String used to generate a QR code for the token. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidForWorkEnrollmentProfile",
  "accountId": "String",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "tokenValue": "String",
  "tokenExpirationDateTime": "String (timestamp)",
  "enrolledDeviceCount": 1024,
  "qrCodeContent": "String",
  "qrCodeImage": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "String",
    "value": "binary"
  }
}
```
