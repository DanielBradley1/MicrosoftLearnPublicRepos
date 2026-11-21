<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageactivationerror -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackageActivationError resource type

This reference describes only the beta contract. Select **beta** to view it; availability depends on the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A code/message value used by [copilotPackageActivationStep](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageactivationstep) and [copilotPackageActivationResult](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageactivationresult). A warning inside a successful activation response can carry this value.

It isn't a redefinition of the Microsoft Graph HTTP error envelope. Normal non-2xx activation responses don't return the composite workflow result, and the root workflow `error` property isn't populated on the normal successful Graph path.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `code` | String | Nullable. Service-specific workflow error code. Remains a string rather than an invented closed enumeration. |
| `message` | String | Nullable. Curated developer-readable explanation, not a stable machine key or raw downstream error. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackageActivationError",
  "code": "String",
  "message": "String"
}
```
