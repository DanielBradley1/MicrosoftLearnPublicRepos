<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage -->
<!-- Sitemap-Last-Modified: 2026-10-02 -->

# copilotPackage resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Entity that represents a Copilot package available within a tenant, containing basic metadata and configuration information for package management.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| `agentIdentityId` | String | The Microsoft Entra Agent ID of the agent. |
| `appId` | String | Associated Microsoft Entra AD application registration ID for this package. |
| `assetId` | String | Identifier used to reference this package in the asset store. |
| `availableTo` | [packageAllowStatus](#packageallowstatus-enumeration) | Enum value specifying which users or groups within the tenant can access this package \(`allowedForAll`, `allowedForSome`, `allowedForNone`\). |
| `createdDateTime` | DateTimeOffset | The date and time that the agent package was created. |
| `deployedTo` | [packageAcquireStatus](#packageacquirestatus-enumeration) | Enum value indicating the current deployment scope of the package within the tenant \(`acquiredForAll`, `acquiredForSome`, `acquiredForNone`\). |
| `displayName` | String | Human-readable name of the package shown to users and administrators. |
| `elementTypes` | String collection | Collection of element types contained within this package \(for example, `bot`, `declarativeAgent`\). |
| `governanceMetadata` | String | The agentic classification of the agent. Possible values are: `PromptAgent`, `HostedAgent`, `WorkflowAgent`, `ManagedAgent`, `Unmanaged`, and `AIApp`. |
| `id` | String | Unique identifier for the Copilot package within the tenant. |
| `isBlocked` | Boolean | Boolean flag indicating whether the package is administratively blocked from use within the tenant. |
| `lastModifiedDateTime` | DateTimeOffset | Timestamp of the last modification made to the package configuration or metadata. |
| `manifestId` | String | Unique identifier declared in the package manifest. Not updatable after creation. |
| `manifestVersion` | String | Version of the manifest schema used to define this package. Not updatable after creation. |
| `platform` | String | The host platform this package targets \(for example, `teams`, `outlook`, `web`\). Supports $filter with eq. |
| `publisher` | String | Name of the organization or entity that published this package. |
| `requestStatus` | [copilotPackageRequestStatus](#copilotpackagerequeststatus-enumeration) | Nullable. Status of the request associated with this package. Supports `$filter` with `eq` on [List packages](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackages-list). |
| `requestType` | [copilotPackageRequestType](#copilotpackagerequesttype-enumeration) | Nullable. Kind of request associated with this package. Supports `$filter` with `eq` on [List packages](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackages-list). |
| `shortDescription` | String | Brief description providing an overview of the package's functionality and purpose. |
| `supportedHosts` | String collection | Collection of host applications where this package can be used \(for example, `teams`, `outlook`, `sharePoint`\). |
| `type` | [packageType](#packagetype-enumeration) | The type classification of the package, indicating whether it's first-party, third-party, shared, or LOB. |
| `version` | String | Version string of the package \(for example, `1.2.3`\). Not updatable after creation. |
| `zipFile` | Stream | The Copilot package file. |

### copilotPackageRequestStatus enumeration

| Value | Description |
| :--- | :--- |
| `pending` | The request is open and waiting for an administrator to act on it. |
| `approved` | An administrator approved the request. |
| `rejected` | An administrator rejected the request. |
| `unknownFutureValue` | [Evolvable sentinel value](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). |

### copilotPackageRequestType enumeration

| Value | Description |
| :--- | :--- |
| `publish` | A user asked for a new package to be published to the organization catalog. |
| `activate` | A user asked for a package that's present in the catalog to be activated for use. |
| `access` | A user asked to be granted access to a package that's already active in the organization. |
| `update` | A user asked for an already published package to be updated to a newer version. |
| `unknownFutureValue` | [Evolvable sentinel value](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). |

### packageAllowStatus enumeration

| Value | Description |
| :--- | :--- |
| `allowedForNone` | Not available to any users. |
| `allowedForSome` | Available to some users/groups. |
| `allowedForAll` | Available to all users. |
| `unknownFutureValue` | [Evolvable sentinel value](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). |

### packageAcquireStatus enumeration

| Value | Description |
| :--- | :--- |
| `acquiredForNone` | Not deployed to any users. |
| `acquiredForSome` | Deployed to some users/groups. |
| `acquiredForAll` | Deployed to all users. |
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
  "agentIdentityId": "String",
  "appId": "String",
  "assetId": "String",
  "availableTo": "String",
  "createdDateTime": "DateTimeOffset",
  "deployedTo": "String",
  "displayName": "String",
  "elementTypes": ["String"],
  "governanceMetadata": "String",
  "id": "String",
  "isBlocked": "Boolean",
  "lastModifiedDateTime": "DateTimeOffset",
  "manifestId": "String",
  "manifestVersion": "String",
  "platform": "String",
  "publisher": "String",
  "requestStatus": "String",
  "requestType": "String",
  "shortDescription": "String",
  "supportedHosts": ["String"],
  "type": "String",
  "version": "String",
  "zipFile": "Stream"
}
```
