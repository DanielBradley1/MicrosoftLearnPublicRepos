<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageactivationprincipal -->
<!-- Sitemap-Last-Modified: 2026-11-18 -->

# copilotPackageActivationPrincipal resource type

This reference describes only the beta contract. Select **beta** to view it; availability depends on the matching schema and backend release.

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A selected user or group in [copilotPackageAgentManagerScope](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageagentmanagerscope). The reviewed native Activate contract uses this narrow principal shape, not the broader Publish principal vocabulary.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | Required and non-nullable. Nonblank user or group object identifier, not a display name, contact address, application client ID, or request identifier. The native adapter's input check doesn't establish a separate GUID-format guarantee. |
| `type` | accessEntityType | Required and non-nullable. The existing principal-type enumeration. Accepted inputs are `user` and `group`; `unknownFutureValue` isn't an accepted input. |

### accessEntityType enumeration

| Value | Description |
| :--- | :--- |
| `user` | A user object. |
| `group` | A group object. |
| `unknownFutureValue` | Reserved for enum evolution; not an activation-audience input. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackageActivationPrincipal",
  "id": "String",
  "type": "String"
}
```
