<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# device resource type

Namespace: microsoft.graph

Represents a device registered in the organization. Devices are created in the cloud using the Device Registration Service or by Intune. They're used by conditional access policies for multi-factor authentication. These devices can range from desktop and laptop machines to phones and tablets. Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

This resource is an open type that allows additional properties beyond those documented here.

This resource supports:

- Adding your own data to custom properties as [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview).
- Using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a [delta](https://learn.microsoft.com/en-us/graph/api/user-delta?view=graph-rest-1.0) function.
- [OData query capabilities](https://learn.microsoft.com/en-us/graph/query-parameters) including `$select`, `$filter`, `$search`, and `$top`. Specific usages are supported only with [Advanced query capabilities](https://learn.microsoft.com/en-us/graph/aad-advanced-queries#group-properties).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/device-list?view=graph-rest-1.0) | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) collection | Retrieve a list of devices registered in the directory. |
| [Create](https://learn.microsoft.com/en-us/graph/api/device-post-devices?view=graph-rest-1.0) | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | Register a new device in the directory. |
| [Get](https://learn.microsoft.com/en-us/graph/api/device-get?view=graph-rest-1.0) | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | Read properties and relationships of a device object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/device-update?view=graph-rest-1.0) | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) | Update the properties of a device object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/device-delete?view=graph-rest-1.0) | None | Delete a device object. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/device-delta?view=graph-rest-1.0) | [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) collection | Get incremental changes for devices. |
| [List member of](https://learn.microsoft.com/en-us/graph/api/device-list-memberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | List the groups and administrative units that the device is a direct member of. |
| [List transitive member of](https://learn.microsoft.com/en-us/graph/api/device-list-transitivememberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | List the groups and administrative units that the device is a member of. This operation is transitive. |
| [List registered owners](https://learn.microsoft.com/en-us/graph/api/device-list-registeredowners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the users that are registered owners of the device from the registeredOwners navigation property. |
| [Add registered owners](https://learn.microsoft.com/en-us/graph/api/device-post-registeredowners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Add registered owners of the device. |
| [Remove registered owners](https://learn.microsoft.com/en-us/graph/api/device-delete-registeredowners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Delete registered owners from the device. |
| [List registered users](https://learn.microsoft.com/en-us/graph/api/device-list-registeredusers?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the registered users of the device from the registeredUsers navigation property. |
| [Add registered users](https://learn.microsoft.com/en-us/graph/api/device-post-registeredusers?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Add registered users of the device . |
| [Remove registered users](https://learn.microsoft.com/en-us/graph/api/device-delete-registeredusers?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Remove registered users from the device . |
| [Check member objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmemberobjects?view=graph-rest-1.0) | String collection | Check for membership in a list of groups, directory role, or administrative unit objects. |
| [Get member objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmemberobjects?view=graph-rest-1.0) | String collection | Return all groups, administrative units, and directory roles that the device is a member of. The check is transitive. |

## Properties

Important

Specific usage of `$filter` and the `$search` query parameter is supported only when you use the **ConsistencyLevel** header set to `eventual` and `$count`. For more information, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries#device-properties).

| Property | Type | Description |
| :--- | :--- | :--- |
| accountEnabled | Boolean | `true` if the account is enabled; otherwise, `false`. Required. Default is `true`.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `not`, `in`\). Only callers with at least the Cloud Device Administrator role can set this property. |
| alternativeSecurityIds | [alternativeSecurityId](https://learn.microsoft.com/en-us/graph/api/resources/alternativesecurityid?view=graph-rest-1.0) collection | For internal use only. Not nullable. Supports `$filter` \(`eq`, `not`, `ge`, `le`\). |
| approximateLastSignInDateTime | DateTimeOffset | The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, and `eq` on `null` values\) and `$orderby`. |
| complianceExpirationDateTime | DateTimeOffset | The timestamp when the device is no longer deemed compliant. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| deviceCategory | String | User-defined property set by Intune to automatically add devices to groups and simplify managing devices. |
| deviceId | String | Unique identifier set by Azure Device Registration Service at the time of registration. This alternate key can be used to reference the device object. Supports `$filter` \(`eq`, `ne`, `not`, `startsWith`\). |
| deviceMetadata | String | For internal use only. Set to `null`. |
| deviceOwnership | String | Ownership of the device. Intune sets this property. The possible values are: `unknown`, `company`, `personal`. |
| deviceVersion | Int32 | For internal use only. |
| displayName | String | The display name for the device. Maximum length is 256 characters. Required. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` on `null` values\), `$search`, and `$orderby`. |
| enrollmentProfileName | String | Enrollment profile applied to the device. For example, `Apple Device Enrollment Profile`, `Device enrollment - Corporate device identifiers`, or `Windows Autopilot profile name`. This property is set by Intune. |
| enrollmentType | String | Enrollment type of the device. Intune sets this property. The possible values are: `unknown`, `userEnrollment`, `deviceEnrollmentManager`, `appleBulkWithUser`, `appleBulkWithoutUser`, `windowsAzureADJoin`, `windowsBulkUserless`, `windowsAutoEnrollment`, `windowsBulkAzureDomainJoin`, `windowsCoManagement`, `windowsAzureADJoinUsingDeviceAuth`,`appleUserEnrollment`, `appleUserEnrollmentWithServiceAccount`.  <br>  <br>**NOTE:** This property might return other values apart from those listed. |
| extensionAttributes | [onPremisesExtensionAttributes](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesextensionattributes?view=graph-rest-1.0) | Contains extension attributes 1-15 for the device. The individual extension attributes aren't selectable. These properties are mastered in the cloud and can be set during creation or update of a device object in Microsoft Entra ID.  <br>  <br>Supports `$filter` \(`eq`, `not`, `startsWith`, and `eq` on `null` values\). |
| id | String | The unique identifier for the device. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). Key, Not nullable. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `in`\). |
| isCompliant | Boolean | `true` if the device complies with Mobile Device Management \(MDM\) policies; otherwise, `false`. Read-only. This can only be updated by Intune for any device OS type or by an [approved MDM app](https://learn.microsoft.com/en-us/windows/client-management/mdm/azure-active-directory-integration-with-mdm) for Windows OS devices. Supports `$filter` \(`eq`, `ne`, `not`\). |
| isManaged | Boolean | `true` if the device is managed by a Mobile Device Management \(MDM\) app; otherwise, `false`. This can only be updated by Intune for any device OS type or by an [approved MDM app](https://learn.microsoft.com/en-us/windows/client-management/mdm/azure-active-directory-integration-with-mdm) for Windows OS devices. Supports `$filter` \(`eq`, `ne`, `not`\). |
| isManagementRestricted | Boolean | Indicates whether the device is a member of a restricted management administrative unit. If not set, the default value is `null` and the default behavior is false. Read-only.  <br>  <br>To manage a device that's a member of a restricted management administrative unit, the administrator or calling app must be assigned a Microsoft Entra role at the scope of the restricted management administrative unit.  <br>  <br>Requires `$select` to retrieve. |
| isRooted | Boolean | `true` if the device is rooted or jail-broken. This property can only be updated by Intune. |
| managementType | String | The management channel of the device. This property is set by Intune. The possible values are: `eas`, `mdm`, `easMdm`, `intuneClient`, `easIntuneClient`, `configurationManagerClient`, `configurationManagerClientMdm`, `configurationManagerClientMdmEas`, `unknown`, `jamf`, `googleCloudDevicePolicyController`. |
| manufacturer | String | Manufacturer of the device. Read-only. |
| mdmAppId | String | Application identifier used to register device into MDM. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `startsWith`\). |
| model | String | Model of the device. Read-only. |
| onPremisesLastSyncDateTime | DateTimeOffset | The last time at which the object was synced with the on-premises directory. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`\). |
| onPremisesSecurityIdentifier | String | The on-premises security identifier \(SID\) for the user who was synchronized from on-premises to the cloud. Read-only. Requires `$select` to retrieve. Supports `$filter` \(`eq`\). |
| onPremisesSyncEnabled | Boolean | `true` if this object is synced from an on-premises directory; `false` if this object was originally synced from an on-premises directory but is no longer synced; `null` if this object has never been synced from an on-premises directory \(default\). Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `in`, and `eq` on `null` values\). |
| operatingSystem | String | The type of operating system on the device. Required. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `startsWith`, and `eq` on `null` values\). |
| operatingSystemVersion | String | The version of the operating system on the device. Required. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `startsWith`, and `eq` on `null` values\). |
| physicalIds | String collection | For internal use only. Not nullable. Supports `$filter` \(`eq`, `not`, `ge`, `le`, `startsWith`,`/$count eq 0`, `/$count ne 0`\). |
| profileType | deviceProfileType | The profile type of the device. Possible values: `RegisteredDevice` \(default\), `SecureVM`, `Printer`, `Shared`, `IoT`. |
| registrationDateTime | DateTimeOffset | Date and time of when the device was registered. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| systemLabels | String collection | List of labels applied to the device by the system. Supports `$filter` \(`/$count eq 0`, `/$count ne 0`\). |
| trustType | String | Type of trust for the joined device. Read-only. Possible values: `Workplace` \(indicates *bring your own personal devices*\), `AzureAd` \(Cloud-only joined devices\), `ServerAd` \(on-premises domain joined devices joined to Microsoft Entra ID\). For more information, see [Introduction to device management in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/device-management-introduction). Supports `$filter` \(`eq`, `ne`, `not`, `in`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for the device. Read-only. Nullable. |
| memberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Groups and administrative units that this device is a member of. Read-only. Nullable. Supports `$expand`. |
| registeredOwners | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The user that cloud joined the device or registered their personal device. The registered owner is set at the time of registration. Read-only. Nullable. Supports `$expand`. |
| registeredUsers | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Collection of registered users of the device. For cloud joined devices and registered personal devices, registered users are set to the same value as registered owners at the time of registration. Read-only. Nullable. Supports `$expand`. |
| transitiveMemberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Groups and administrative units that the device is a member of. This operation is transitive. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "accountEnabled": "Boolean",
  "alternativeSecurityIds": [{"@odata.type": "microsoft.graph.alternativeSecurityId"}],
  "approximateLastSignInDateTime": "String (timestamp)",
  "complianceExpirationDateTime": "String (timestamp)",
  "deviceCategory": "String",
  "deviceId": "String",
  "deviceMetadata": "String",
  "deviceOwnership": "String",
  "deviceVersion": "Int32",
  "displayName": "String",
  "enrollmentProfileName": "String",
  "enrollmentType": "String",
  "extensionAttributes": {"@odata.type": "microsoft.graph.onPremisesExtensionAttributes"},
  "id": "String (identifier)",
  "isCompliant": "Boolean",
  "isManaged": "Boolean",
  "isManagementRestricted": "Boolean",
  "isRooted": "Boolean",
  "managementType": "String",
  "manufacturer": "String",
  "mdmAppId": "String",
  "model": "String",
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSecurityIdentifier": "String",
  "onPremisesSyncEnabled": "Boolean",
  "operatingSystem": "String",
  "operatingSystemVersion": "String",
  "physicalIds": ["String"],
  "profileType": "String",
  "registrationDateTime": "String (timestamp)",
  "systemLabels": ["String"],
  "trustType": "String"
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
