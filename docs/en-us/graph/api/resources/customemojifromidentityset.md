<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customemojifromidentityset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# customEmojiFromIdentitySet resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the identity of the user who created a [custom emoji](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta) in the teamwork messaging of the organization.

Inherits from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| application | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | If present, represents the application that created the emoji. Inherited from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta). |
| device | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | Not implemented. Don't use. Inherited from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta). |
| user | [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-beta) | If present, represents the user who created the emoji. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.customEmojiFromIdentitySet",
    "user": {
        "@odata.type": "microsoft.graph.teamworkUserIdentity"
    },
    "application": {
        "@odata.type": "microsoft.graph.identity"
    },
    "device": {
        "@odata.type": "microsoft.graph.identity"
    }
}
```

## Related content

- [teamworkCustomEmoji resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamworkcustomemoji?view=graph-rest-beta)
- [identitySet resource type](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta)
