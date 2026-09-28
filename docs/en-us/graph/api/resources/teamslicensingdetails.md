<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamslicensingdetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-09 -->

# teamsLicensingDetails resource type

Namespace: microsoft.graph

A container where you can find all the different Microsoft Teams license details for each user in the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hasTeamsLicense | Boolean | Indicates whether the user has a valid license to use Microsoft Teams. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "hasTeamsLicense": "Boolean",
}
```

## Related content

- [teamwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamwork?view=graph-rest-1.0)
- [userTeamwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-1.0)
