<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamdiscoverysettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamDiscoverySettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides settings to enable others to configure [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-beta) discoverability. You can only modify discovery settings for private teams.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| showInTeamsSearchAndSuggestions | Boolean | If set to true, the team is visible via search and suggestions from the Teams client. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "showInTeamsSearchAndSuggestions": true
}
```
