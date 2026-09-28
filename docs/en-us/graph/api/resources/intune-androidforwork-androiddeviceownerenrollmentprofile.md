<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidDeviceOwnerEnrollmentProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Enrollment Profile used to enroll Android Enterprise devices using Google's Cloud Management.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidDeviceOwnerEnrollmentProfiles](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androiddeviceownerenrollmentprofile-list?view=graph-rest-beta) | [androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile?view=graph-rest-beta) collection | List properties and relationships of the [androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile?view=graph-rest-beta) objects. |
| [Get androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androiddeviceownerenrollmentprofile-get?view=graph-rest-beta) | [androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile?view=graph-rest-beta) | Read properties and relationships of the [androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile?view=graph-rest-beta) object. |
| [Create androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androiddeviceownerenrollmentprofile-create?view=graph-rest-beta) | [androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile?view=graph-rest-beta) | Create a new [androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile?view=graph-rest-beta) object. |
| [Delete androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androiddeviceownerenrollmentprofile-delete?view=graph-rest-beta) | None | Deletes a [androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile?view=graph-rest-beta). |
| [Update androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androiddeviceownerenrollmentprofile-update?view=graph-rest-beta) | [androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile?view=graph-rest-beta) | Update the properties of a [androidDeviceOwnerEnrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentprofile?view=graph-rest-beta) object. |
| [revokeToken action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androiddeviceownerenrollmentprofile-revoketoken?view=graph-rest-beta) | None |  |
| [createToken action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androiddeviceownerenrollmentprofile-createtoken?view=graph-rest-beta) | None |  |
| [getDefaultTeamsDeviceNonGmsEnrollmentProfile action](https://learn.microsoft.com/en-us/graph/api/api/intune-androidforwork-androiddeviceownerenrollmentprofile-getdefaultteamsdevicenongmsenrollmentprofile.md?view=graph-rest-beta) | [enrollmentProfileForNonGmsTeamsDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-enrollmentprofilefornongmsteamsdevice.md?view=graph-rest-beta) |  |
| [setEnrollmentTimeDeviceMembershipTarget action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androiddeviceownerenrollmentprofile-setenrollmenttimedevicemembershiptarget?view=graph-rest-beta) | [enrollmentTimeDeviceMembershipTargetResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmenttimedevicemembershiptargetresult?view=graph-rest-beta) |  |
| [retrieveEnrollmentTimeDeviceMembershipTarget action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androiddeviceownerenrollmentprofile-retrieveenrollmenttimedevicemembershiptarget?view=graph-rest-beta) | [enrollmentTimeDeviceMembershipTargetResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmenttimedevicemembershiptargetresult?view=graph-rest-beta) |  |
| [clearEnrollmentTimeDeviceMembershipTarget action](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androiddeviceownerenrollmentprofile-clearenrollmenttimedevicemembershiptarget?view=graph-rest-beta) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accountId | String | Tenant GUID the enrollment profile belongs to. |
| id | String | Unique GUID for the enrollment profile. |
| displayName | String | Display name for the enrollment profile. |
| description | String | Description for the enrollment profile. |
| enrollmentMode | [androidDeviceOwnerEnrollmentMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmentmode?view=graph-rest-beta) | The enrollment mode of devices that use this enrollment profile. Possible values are: `corporateOwnedDedicatedDevice`, `corporateOwnedFullyManaged`, `corporateOwnedWorkProfile`, `corporateOwnedAOSPUserlessDevice`, `corporateOwnedAOSPUserAssociatedDevice`. |
| enrollmentTokenType | [androidDeviceOwnerEnrollmentTokenType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androiddeviceownerenrollmenttokentype?view=graph-rest-beta) | The enrollment token type for an enrollment profile. Possible values are: `default`, `corporateOwnedDedicatedDeviceWithAzureADSharedMode`, `deviceStaging`. |
| createdDateTime | DateTimeOffset | Date time the enrollment profile was created. |
| lastModifiedDateTime | DateTimeOffset | Date time the enrollment profile was last modified. |
| tokenValue | String | Value of the most recently created token for this enrollment profile. |
| tokenCreationDateTime | DateTimeOffset | Date time the most recently created token was created. |
| tokenExpirationDateTime | DateTimeOffset | Date time the most recently created token will expire. |
| enrolledDeviceCount | Int32 | Total number of Android devices that have enrolled using this enrollment profile. |
| enrollmentTokenUsageCount | Int32 | Total number of AOSP devices that have enrolled using the current token. Valid values 0 to 20000 |
| qrCodeContent | String | String used to generate a QR code for the token. |
| qrCodeImage | [mimeContent](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mimecontent?view=graph-rest-beta) | String used to generate a QR code for the token. |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. |
| configureWifi | Boolean | Boolean that indicates that the Wi-Fi network should be configured during device provisioning. When set to TRUE, device provisioning will use Wi-Fi related properties to automatically connect to Wi-Fi networks. When set to FALSE or undefined, other Wi-Fi related properties will be ignored. Default value is TRUE. Returned by default. |
| wifiSsid | String | String that contains the wi-fi login ssid |
| wifiPassword | String | String that contains the wi-fi login password |
| wifiSecurityType | [aospWifiSecurityType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-aospwifisecuritytype?view=graph-rest-beta) | String that contains the wi-fi security type. Possible values are: `none`, `wpa`, `wep`. |
| wifiHidden | Boolean | Boolean that indicates if hidden wifi networks are enabled |
| isTeamsDeviceProfile | Boolean | Boolean indicating if this profile is an Android AOSP for Teams device profile. |
| deviceNameTemplate | String | Indicates the device name template used for the enrolled Android devices. The maximum length allowed for this property is 63 characters. The template expression contains normal text and tokens, including the serial number of the device, user name, device type, upn prefix, or a randomly generated number. Supported Tokens for device name templates are: \(for device naming template expression\): {{SERIAL}}, {{SERIALLAST4DIGITS}}, {{ENROLLMENTDATETIME}}, {{USERNAME}}, {{DEVICETYPE}}, {{UPNPREFIX}}, {{rand:x}}. Supports: $select, $top, $skip. $Search, $orderBy and $filter are not supported. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidDeviceOwnerEnrollmentProfile",
  "accountId": "String",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "enrollmentMode": "String",
  "enrollmentTokenType": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "tokenValue": "String",
  "tokenCreationDateTime": "String (timestamp)",
  "tokenExpirationDateTime": "String (timestamp)",
  "enrolledDeviceCount": 1024,
  "enrollmentTokenUsageCount": 1024,
  "qrCodeContent": "String",
  "qrCodeImage": {
    "@odata.type": "microsoft.graph.mimeContent",
    "type": "String",
    "value": "binary"
  },
  "roleScopeTagIds": [
    "String"
  ],
  "configureWifi": true,
  "wifiSsid": "String",
  "wifiPassword": "String",
  "wifiSecurityType": "String",
  "wifiHidden": true,
  "isTeamsDeviceProfile": true,
  "deviceNameTemplate": "String"
}
```
