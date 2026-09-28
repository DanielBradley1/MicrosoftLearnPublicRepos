<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityinboundaccess?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# m365CapabilityInboundAccess resource type

Namespace: microsoft.graph

Represents the inbound access settings for a cross-tenant Microsoft 365 capability. This type defines whether the capability should be allowed or blocked and specifies the resource scopes for the capability. This resource is used as the **inboundAccess** property of the [m365CapabilityBase](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilitybase?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isAllowed | Boolean | Indicates whether this capability should be allowed or blocked for inbound access. |
| resourceScopes | [m365CapabilityResourceScopes](https://learn.microsoft.com/en-us/graph/api/resources/m365capabilityresourcescopes?view=graph-rest-1.0) | Specifies the included and excluded resource scopes for the capability. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.m365CapabilityInboundAccess",
  "isAllowed": "Boolean",
  "resourceScopes": { "@odata.type": "microsoft.graph.m365CapabilityResourceScopes" }
}
```
