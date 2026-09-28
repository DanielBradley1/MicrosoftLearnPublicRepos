<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackageupdateresponse -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# copilotPackageUpdateResponse complex type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents the response returned when a Copilot package is uploaded or updated.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | Unique identifier of the package that was created or updated through package management. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.copilotPackageUpdateResponse",
  "id": "String"
}
```
