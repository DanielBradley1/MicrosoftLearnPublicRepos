<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagedetail -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# copilotPackageDetail resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Extended entity that inherits from [copilotPackage](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage) and provides comprehensive detailed information about a Copilot package.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Methods

| Method | Return type | Description |
| --- | --- | --- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackages-list) | `copilotPackageDetail` collection | Get the available Copilot packages. |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagedetail-get) | `copilotPackageDetail` | Read the properties and relationships of a `copilotPackageDetail` object. |

| Method | Return type | Description |
| --- | --- | --- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackages-list) | `copilotPackageDetail` collection | Get the available Copilot packages. |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagedetail-get) | `copilotPackageDetail` | Read the properties and relationships of a `copilotPackageDetail` object. |
| [Update](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagedetail-update) | `copilotPackageDetail` | Update a `copilotPackageDetail` object. |
| [Block](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackage-block) | None | Block a Copilot package to prevent its usage. |
| [Reassign](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackage-reassign) | None | Reassign ownership of a Copilot package to a different user. |
| [Unblock](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackage-unblock) | None | Unblock a Copilot package to allow its usage. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| `acquireUsersAndGroups` | [packageAccessEntity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/packageaccessentity) collection | Collection of users and groups that have acquired or installed this package for use within the tenant. |
| `allowedUsersAndGroups` | [packageAccessEntity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/packageaccessentity) collection | Collection of users and groups that are currently permitted to access and use this package within the tenant. |
| `appId` | String | Associated Azure AD application registration ID for this package. Inherited from copilotPackage. |
| `assetId` | String | Identifier used to reference this package in the asset store. Inherited from copilotPackage. |
| `availableTo` | [packageStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage#packagestatus-enumeration) | Enum value specifying which users or groups within the tenant can access this package. Inherited from copilotPackage. |
| `categories` | String collection | Collection of category tags that classify the package by functionality or domain \(e.g., Development, Productivity\). |
| `deployedTo` | [packageStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage#packagestatus-enumeration) | Enum value indicating the current deployment scope of the package. Inherited from copilotPackage. |
| `displayName` | String | Human-readable name of the package shown to users and administrators. Inherited from copilotPackage. |
| `elementDetails` | [packageElementDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/packageelementdetail) collection | Collection of detailed information about each element contained within the package, including type and configuration. |
| `elementTypes` | String collection | Collection of element types contained within this package. Inherited from copilotPackage. |
| `id` | String | Unique identifier for the Copilot package within the tenant. Inherited from copilotPackage. |
| `isBlocked` | Boolean | Boolean flag indicating whether the package has been administratively blocked. Inherited from copilotPackage. |
| `lastModifiedDateTime` | DateTimeOffset | Timestamp of the last modification made to the package. Inherited from copilotPackage. |
| `longDescription` | String | Comprehensive description providing detailed information about the package functionality, features, and usage. |
| `manifestId` | String | Unique identifier declared in the package manifest. Not updatable after creation. Inherited from copilotPackage. |
| `manifestVersion` | String | Version of the manifest schema used to define this package. Not updatable. Inherited from copilotPackage. |
| `platform` | String | The host platform this package targets \(e.g., teams, outlook, web\). Inherited from copilotPackage. |
| `publisher` | String | Name of the organization or entity that published this package. Inherited from copilotPackage. |
| `sensitivity` | String | Sensitivity classification level indicating data handling requirements or compliance restrictions for the package. |
| `shortDescription` | String | Brief description providing an overview of the package's functionality. Inherited from copilotPackage. |
| `supportedHosts` | String collection | Collection of host applications where this package can be used. Inherited from copilotPackage. |
| `type` | [packageType](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage#packagetype-enumeration) | The type classification of the package. Inherited from copilotPackage. |
| `version` | String | Version string of the package \(e.g., 1.2.3\). Not updatable after creation. Inherited from copilotPackage. |
| `zipFile` | Stream | The Copilot package file. Inherited from copilotPackage. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackageDetail",
  "id": "String",
  "displayName": "String",
  "type": "String",
  "shortDescription": "String",
  "isBlocked": "Boolean",
  "availableTo": "String",
  "deployedTo": "String",
  "lastModifiedDateTime": "DateTimeOffset",
  "supportedHosts": ["String"],
  "elementTypes": ["String"],
  "publisher": "String",
  "platform": "String",
  "version": "String",
  "manifestVersion": "String",
  "manifestId": "String",
  "appId": "String",
  "assetId": "String",
  "longDescription": "String",
  "categories": ["String"],
  "sensitivity": "String",
  "acquireUsersAndGroups": [
    {
      "@odata.type": "microsoft.graph.packageAccessEntity"
    }
  ],
  "allowedUsersAndGroups": [
    {
      "@odata.type": "microsoft.graph.packageAccessEntity"
    }
  ],
  "elementDetails": [
    {
      "@odata.type": "microsoft.graph.packageElementDetail"
    }
  ]
}
```
