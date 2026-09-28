<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityresourcescopes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# m365CapabilityResourceScopes resource type

Namespace: microsoft.graph

Specifies the included and excluded resource scopes for a cross-tenant capability. This type defines which resources are in scope for the capability and which resources are explicitly excluded. This resource is used as the **resourceScopes** property of the [m365CapabilityInboundAccess](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityinboundaccess?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excluded | [m365CapabilityResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityresourcescope?view=graph-rest-1.0) collection | Resources to exclude from the scope. If a resource appears in both **included** and **excluded**, the **excluded** property takes precedence. |
| included | [m365CapabilityResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityresourcescope?view=graph-rest-1.0) collection | Resources to include in the scope. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.m365CapabilityResourceScopes",
  "included": [
    { "@odata.type": "microsoft.graph.m365CapabilityResourceScope" }
  ],
  "excluded": [
    { "@odata.type": "microsoft.graph.m365CapabilityResourceScope" }
  ]
}
```
