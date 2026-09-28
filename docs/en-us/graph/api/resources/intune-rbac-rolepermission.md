<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolepermission?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# rolePermission resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains the set of ResourceActions determining the allowed and not allowed permissions for each role.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resourceActions | [resourceAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceaction?view=graph-rest-1.0) collection | Resource Actions each containing a set of allowed and not allowed permissions. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.rolePermission",
  "resourceActions": [
    {
      "@odata.type": "microsoft.graph.resourceAction",
      "allowedResourceActions": [
        "String"
      ],
      "notAllowedResourceActions": [
        "String"
      ]
    }
  ]
}
```
