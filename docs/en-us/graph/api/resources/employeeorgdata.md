<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/employeeorgdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# employeeOrgData resource type

Namespace: microsoft.graph

Represents organization data associated with a user. The **employeeOrgData** property of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) entity is a collection of organization attributes. Include both property values when updating **employeeOrgData**; if you omit any, the system sets them to `null`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| division | String | The name of the division in which the user works.  <br>  <br>Requires `$select` to retrieve. Supports `$filter`. |
| costCenter | String | The cost center associated with the user.  <br>  <br>Requires `$select` to retrieve. Supports `$filter`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "costCenter": "string",
  "division": "string"
}
```
