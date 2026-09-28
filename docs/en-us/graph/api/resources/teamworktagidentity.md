<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworktagidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkTagIdentity resource type

Namespace: microsoft.graph

Represents a **tag** in Microsoft Teams. Tags allow users to quickly connect to subset of users in a team. For details about tag management in Microsoft Teams, see [Manage tags in Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/manage-tags).

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). Display name of the tag. |
| id | String | Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). ID of the tag. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkTagIdentity",
  "id": "String (identifier)",
  "displayName": "String"
}
```
