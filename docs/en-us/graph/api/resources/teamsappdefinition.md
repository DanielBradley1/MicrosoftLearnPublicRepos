<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# teamsAppDefinition resource type

Namespace: microsoft.graph

Represents the details of a version of a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authorization | [teamsAppAuthorization](https://learn.microsoft.com/en-us/graph/api/resources/teamsappauthorization?view=graph-rest-1.0) | Authorization requirements specified in the Teams app manifest. |
| description | String | Verbose description of the application. |
| displayName | String | The name of the app provided by the app developer. |
| id | String | A unique ID \(not the Teams app ID\). |
| publishingState | String | The published status of a specific version of a Teams app. The possible values are:  <br>`submitted`—The specific version of the Teams app was submitted and is under review.  <br>`published`—The request to publish the specific version of the Teams app was approved by the admin and the app is published.  <br>`rejected`—The admin rejected the request to publish the specific version of the Teams app. |
| shortDescription | String | Short description of the application. |
| teamsAppId | String | The ID from the Teams app manifest. |
| version | String | The version number of the application. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| bot | [teamworkBot](https://learn.microsoft.com/en-us/graph/api/resources/teamworkbot?view=graph-rest-1.0) | The details of the bot specified in the Teams app manifest. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "authorization": {"@odata.type": "microsoft.graph.teamsAppAuthorization"},
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "publishingState": "String",
  "shortDescription": "String",
  "teamsAppId": "String",
  "version": "String"
}
```

## Related content

- [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0)
- [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0)
- [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0)
