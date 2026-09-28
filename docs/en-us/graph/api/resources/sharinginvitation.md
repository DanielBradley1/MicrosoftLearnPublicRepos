<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharinginvitation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# sharingInvitation resource type

Namespace: microsoft.graph

Groups invitation-related data items into a single structure.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "email": "string",
  "invitedBy": {"@odata.type": "microsoft.graph.identitySet" },
  "signInRequired": true
}
```

## Properties

| Property Name | Type | Description |
| :--- | :--- | :--- |
| email | String | The email address provided for the recipient of the sharing invitation. Read-only. |
| invitedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Provides information about who sent the invitation that created this permission, if that information is available. Read-only. |
| signInRequired | Boolean | If `true` the recipient of the invitation needs to sign in in order to access the shared item. Read-only. |

## Remarks

For more information about the facets on a **driveItem**, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
