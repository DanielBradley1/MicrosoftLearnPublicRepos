<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsPrivacyDataAccessControlItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Specify access control level per privacy data category

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsPrivacyDataAccessControlItems](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsprivacydataaccesscontrolitem-list?view=graph-rest-beta) | [windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem?view=graph-rest-beta) collection | List properties and relationships of the [windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem?view=graph-rest-beta) objects. |
| [Get windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsprivacydataaccesscontrolitem-get?view=graph-rest-beta) | [windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem?view=graph-rest-beta) | Read properties and relationships of the [windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem?view=graph-rest-beta) object. |
| [Create windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsprivacydataaccesscontrolitem-create?view=graph-rest-beta) | [windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem?view=graph-rest-beta) | Create a new [windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem?view=graph-rest-beta) object. |
| [Delete windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsprivacydataaccesscontrolitem-delete?view=graph-rest-beta) | None | Deletes a [windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem?view=graph-rest-beta). |
| [Update windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsprivacydataaccesscontrolitem-update?view=graph-rest-beta) | [windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem?view=graph-rest-beta) | Update the properties of a [windowsPrivacyDataAccessControlItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesscontrolitem?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of WindowsPrivacyDataAccessControlItem. |
| accessLevel | [windowsPrivacyDataAccessLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydataaccesslevel?view=graph-rest-beta) | This indicates an access level for the privacy data category to which the specified application will be given to. Possible values are: `notConfigured`, `forceAllow`, `forceDeny`, `userInControl`. |
| dataCategory | [windowsPrivacyDataCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsprivacydatacategory?view=graph-rest-beta) | This indicates a privacy data category to which the specific access control will apply. Possible values are: `notConfigured`, `accountInfo`, `appsRunInBackground`, `calendar`, `callHistory`, `camera`, `contacts`, `diagnosticsInfo`, `email`, `location`, `messaging`, `microphone`, `motion`, `notifications`, `phone`, `radios`, `tasks`, `syncWithDevices`, `trustedDevices`. |
| appPackageFamilyName | String | The Package Family Name of a Windows app. When set, the access level applies to the specified application. |
| appDisplayName | String | The Package Family Name of a Windows app. When set, the access level applies to the specified application. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsPrivacyDataAccessControlItem",
  "id": "String (identifier)",
  "accessLevel": "String",
  "dataCategory": "String",
  "appPackageFamilyName": "String",
  "appDisplayName": "String"
}
```
