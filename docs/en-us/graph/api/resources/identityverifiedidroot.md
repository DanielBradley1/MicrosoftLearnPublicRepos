<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityverifiedidroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# identityVerifiedIdRoot resource type

Namespace: microsoft.graph

Represents the root container for managing Verifiable ID profiles in Microsoft Entra.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List profiles](https://learn.microsoft.com/en-us/graph/api/identityverifiedidroot-list-profiles?view=graph-rest-1.0) | [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) collection | Get a list of the verifiedIdProfile objects and their properties. |
| [Create profile](https://learn.microsoft.com/en-us/graph/api/identityverifiedidroot-post-profiles?view=graph-rest-1.0) | [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) | Create a new verifiedIdProfile object. |
| [Delete profile](https://learn.microsoft.com/en-us/graph/api/identityverifiedidroot-delete-profiles?view=graph-rest-1.0) | None | Delete a verifiedIdProfile object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the identityVerifiedIdRoot. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| profiles | [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0) collection | Profile containing properties about a Verified ID provider and purpose |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityVerifiedIdRoot",
  "id": "String"
}
```
