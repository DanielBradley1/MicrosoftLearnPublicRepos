<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/packageelementdetail -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# packageElementDetail complex type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Provides details for each element type comprising the package.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| `elements` | [packageElement](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/packageelement) collection | List of details for all elements in the package of this type. |
| `elementType` | String | Type of the element \(e.g., CustomEngineCopilot, DeclarativeAgent, Bot\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.packageElementDetail",
  "elements": [
    {
      "@odata.type": "microsoft.graph.packageElement"
    }
  ],
  "elementType": "String"
}
```
