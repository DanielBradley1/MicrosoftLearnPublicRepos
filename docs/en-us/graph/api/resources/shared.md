<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/shared?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# shared resource type

Namespace: microsoft.graph

Indicates that a [drive item](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) was shared with others and includes information about how the item was shared.

If a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) has a non-null **shared** facet, the item was shared.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| owner | [IdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the owner of the shared item. Read-only. |
| sharedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the user who shared the item. Read-only. |
| sharedDateTime | DateTimeOffset | The UTC date and time when the item was shared. Read-only. |
| scope \(deprecated\) | String | Indicates the scope of how the item is shared. The possible values are: `anonymous`, `organization`, or `users`. Read-only. |

Caution

The **scope** property of the shared facet is deprecated and will be removed from the service in the future. Instead, use the `/permissions` endpoint on sites, lists, list items, or drive items to better understand the shared status for a given resource.

### scope property values

| Value | Description |
| :--- | :--- |
| `anonymous` | The item is shared by using a link that works for anyone with the link. |
| `organization` | The item is shared by using a link that works for anyone in the owner's organization. |
| `users` | The item is shared with specific users only. |

## JSON representation

```json
{
  "owner": { "@odata.type": "microsoft.graph.identitySet" },
  "scope": "anonymous | organization | users",
  "sharedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "sharedDateTime": "datetime"
}
```
