<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsapppermissionset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamsAppPermissionSet resource type

Namespace: microsoft.graph

Set of required/granted permissions that can be associated with a Teams app.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resourceSpecificPermissions | [teamsAppResourceSpecificPermission](https://learn.microsoft.com/en-us/graph/api/resources/teamsappresourcespecificpermission?view=graph-rest-1.0) collection | A collection of resource-specific permissions. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAppPermissionSet",
  "resourceSpecificPermissions": [
    {
      "@odata.type": "microsoft.graph.teamsAppResourceSpecificPermission"
    }
  ]
}
```
