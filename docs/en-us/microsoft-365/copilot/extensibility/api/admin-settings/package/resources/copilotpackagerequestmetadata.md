<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagerequestmetadata -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackageRequestMetadata resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents the `requestMetadata` property of [copilotPackageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagedetail).

Use the exact `$select=id,requestMetadata` on [Get package details](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagedetail-get) for the metadata-only projection when its matching release is available. The native `includeRequestMetadata=true` flag isn't a declared Graph query option or a substitute for this selection.

A successful explicit metadata-only result is non-null; an empty `requests` collection means history was loaded with no returned Pending rows. Unreadable history is a failure, not an empty successful fallback. A null value on other detail paths can mean metadata wasn't loaded or wasn't available; it doesn't prove there are no pending requests. The returned rows are snapshots, not independently addressable resources or a complete historical ledger.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `requests` | [copilotPackageRequestInfo](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagerequestinfo) collection | Non-nullable. Returned request snapshots. Empty when metadata was loaded and no requests were found. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackageRequestMetadata",
  "requests": [
    {
      "@odata.type": "microsoft.graph.copilotPackageRequestInfo"
    }
  ]
}
```
