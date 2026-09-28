<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# resourceAction resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Set of allowed and not allowed actions for a resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedResourceActions | String collection | Allowed Actions |
| notAllowedResourceActions | String collection | Not Allowed Actions. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.resourceAction",
  "allowedResourceActions": [
    "String"
  ],
  "notAllowedResourceActions": [
    "String"
  ]
}
```
