<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# copilotPackage resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Entity that represents a Copilot package available within a tenant, containing basic metadata and configuration information for package management.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| `appId` | String | Associated Microsoft Entra AD application registration ID for this package. |
| `assetId` | String | Identifier used to reference this package in the asset store. |
| `availableTo` | [packageStatus](#packagestatus-enumeration) | Enum value specifying which users or groups within the tenant can access this package \(`all`, `some`, `none`\). |
| `deployedTo` | [packageStatus](#packagestatus-enumeration) | Enum value indicating the current deployment scope of the package within the tenant \(`all`, `some`, `none`\). |
| `displayName` | String | Human-readable name of the package shown to users and administrators. |
| `elementTypes` | String collection | Collection of element types contained within this package \(for example, `bot`, `declarativeAgent`\). |
| `id` | String | Unique identifier for the Copilot package within the tenant. |
| `isBlocked` | Boolean | Boolean flag indicating whether the package is administratively blocked from use within the tenant. |
| `lastModifiedDateTime` | DateTimeOffset | Timestamp of the last modification made to the package configuration or metadata. |
| `manifestId` | String | Unique identifier declared in the package manifest. Not updatable after creation. |
| `manifestVersion` | String | Version of the manifest schema used to define this package. Not updatable after creation. |
| `platform` | String | The host platform this package targets \(for example, `teams`, `outlook`, `web`\). Supports $filter with eq. |
| `publisher` | String | Name of the organization or entity that published this package. |
| `shortDescription` | String | Brief description providing an overview of the package's functionality and purpose. |
| `supportedHosts` | String collection | Collection of host applications where this package can be used \(for example, `teams`, `outlook`, `sharePoint`\). |
| `type` | [packageType](#packagetype-enumeration) | The type classification of the package, indicating whether it's first-party, third-party, shared, or LOB. |
| `version` | String | Version string of the package \(for example, `1.2.3`\). Not updatable after creation. |
| `zipFile` | Stream | The Copilot package file. |

### packageStatus enumeration

| Value | Description |
| :--- | :--- |
| `none` | Not available or deployed to any users. |
| `some` | Available or deployed to some users/groups. |
| `all` | Available or deployed to all users. |
| `unknownFutureValue` | [Evolvable sentinel value](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). |

### packageType enumeration

| Value | Description |
| :--- | :--- |
| `microsoft` | Built by Microsoft. |
| `external` | Built by partners. |
| `shared` | Shared in your organization. |
| `custom` | Built by your organization. |
| `unknownFutureValue` | [Evolvable sentinel value](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackage",
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
  "assetId": "String"
}
```
