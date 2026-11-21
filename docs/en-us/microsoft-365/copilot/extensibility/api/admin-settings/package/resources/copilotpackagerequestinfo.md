<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagerequestinfo -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackageRequestInfo resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents one member of the `requests` collection in [copilotPackageRequestMetadata](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagerequestmetadata).

Use this row's `packageRequestType` to distinguish requests for the same package. The package-level `requestType` can summarize a different row.

For [Approve](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackage-approve), use the selected row's `identifier` and exact stored `packageVersion`. The version isn't the package's current/manifest/latest version, and missing information must not be replaced with another row's values. The normalized type identifies the row; callers don't supply a request-type override to approval.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `additionalMetadata` | microsoft.graph.Json | Nullable. Additional collected request data, represented as a JSON object. Read-only. |
| `assignees` | [copilotPackageRequestPrincipal](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagerequestprincipal) collection | Non-nullable. Explicit recipients for a nonpublication request, in source order with duplicates retained; groups aren't expanded. In the matching implementation, publication rows return an empty collection rather than treating requester identity as deployment recipients. Empty doesn't prove no audience. |
| `identifier` | String | Nullable. Opaque business request identifier. Not a Graph resource key, package identifier, or immutable submission identifier; a later request can reuse it. |
| `packageRequestType` | [copilotPackageRequestType](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage#copilotpackagerequesttype-enumeration) | Nullable. This row's normalized request type. Missing or unrecognized source kinds map to `null`. Read-only. |
| `packageVersion` | String | Nullable and computed. Exact nonblank stored version of this individual request, preserved verbatim. Missing/null/empty/whitespace-only source becomes null; no trimming or fallback to the package, latest, manifest, or another row. Required to approve a supported individual request. |
| `requestedBy` | [emailAddress](https://learn.microsoft.com/en-us/graph/api/resources/emailaddress?view=graph-rest-beta&preserve-view=true) | Nullable. In the matching implementation, publication rows use the resolved requester's display profile and return null if it can't be established. Other rows use the first explicit assignee's display contact, or null when no explicit assignee exists; a present assignee can have null contact fields. Not an authorization identifier; a missing contact isn't proof no request exists. |
| `requestedDateTime` | DateTimeOffset | Nullable. Request submission timestamp, when known. Not the package creation time or a concurrency token. |

### copilotPackageRequestType enumeration

The `packageRequestType` property uses the existing [copilotPackageRequestType](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage#copilotpackagerequesttype-enumeration) enumeration.

| Value | Description |
| :--- | :--- |
| `publish` | A request to publish a package. |
| `activate` | A Hire request for a package. |
| `access` | An Access request for a package. |
| `update` | A request to update a published package. |
| `unknownFutureValue` | Evolvable enumeration sentinel. The current row mapper uses `null` for unrecognized source kinds. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackageRequestInfo",
  "additionalMetadata": {
    "@odata.type": "microsoft.graph.Json"
  },
  "assignees": [
    {
      "@odata.type": "microsoft.graph.copilotPackageRequestPrincipal"
    }
  ],
  "identifier": "String",
  "packageRequestType": "String",
  "packageVersion": "String",
  "requestedBy": {
    "@odata.type": "microsoft.graph.emailAddress"
  },
  "requestedDateTime": "DateTimeOffset"
}
```
