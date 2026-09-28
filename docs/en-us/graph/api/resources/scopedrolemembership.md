<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-08 -->

# scopedRoleMembership resource type

Namespace: microsoft.graph

A scoped-role membership describes a user's membership of a directory role that is further scoped to an Administrative Unit. Scoped-role membership provides a mechanism to allow a tenant-wide company administrator to delegate administrative privileges to a user, to manage users and groups in a subset of the organization.

## Methods

Direct queries to this resource aren't supported. See the [administrative units](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) article to see information on how to query for scoped-role memberships, and adding and removing scoped-role memberships.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| administrativeUnitId | string | Unique identifier for the administrative unit that the directory role is scoped to |
| ID | string | Unique identifier for the scoped-role membership. Read-only. |
| roleId | string | Unique identifier for the directory role that the member is in. |
| roleMemberInfo | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Role member identity information. Represents the user that is a member of this scoped-role. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "administrativeUnitId": "string",
  "id": "string (identifier)",
  "roleId": "string",
  "roleMemberInfo": {"@odata.type": "microsoft.graph.identity"}
}
```
