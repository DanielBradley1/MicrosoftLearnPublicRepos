<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/packageelement -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# packageElement complex type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Represents a single element within a Copilot package, containing its unique identifier and definition.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| `definition` | String | Complete definition or manifest of the element as a JSON string. |
| `id` | String | Unique identifier of the element. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.packageElement",
  "definition": "String",
  "id": "String"
}
```
