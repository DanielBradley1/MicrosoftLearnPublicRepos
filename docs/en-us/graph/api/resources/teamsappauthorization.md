<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappauthorization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-18 -->

# teamsAppAuthorization resource type

Namespace: microsoft.graph

The authorization details of a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientAppId | String | The registration ID of the Microsoft Entra app ID associated with the [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0). |
| requiredPermissionSet | [teamsAppPermissionSet](https://learn.microsoft.com/en-us/graph/api/resources/teamsapppermissionset?view=graph-rest-1.0) | Set of permissions required by the [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAppAuthorization",
  "clientAppId": "String",
  "requiredPermissionSet": {"@odata.type": "microsoft.graph.teamsAppPermissionSet"}
}
```
