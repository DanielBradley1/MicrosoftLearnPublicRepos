<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminaccessdetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# delegatedAdminAccessDetails resource type

Namespace: microsoft.graph

Represents the administrative roles that a Microsoft partner has in a customer tenant through a delegated admin relationship and delegated admin access assignment.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| unifiedRoles | [unifiedRole](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrole?view=graph-rest-1.0) collection | The directory roles that the Microsoft partner is assigned in the customer tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegatedAdminAccessDetails",
  "unifiedRoles": [
    {
      "@odata.type": "microsoft.graph.unifiedRole"
    }
  ]
}
```
