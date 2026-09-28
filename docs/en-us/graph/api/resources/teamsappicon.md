<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsappicon?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-08 -->

# teamsAppIcon resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an icon associated with a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get icon](https://learn.microsoft.com/en-us/graph/api/teamsappicon-get?view=graph-rest-beta) | [teamsAppIcon](https://learn.microsoft.com/en-us/graph/api/resources/teamsappicon?view=graph-rest-beta) | Get an icon associated with a specific version of a Teams app. |
| [Get hosted content](https://learn.microsoft.com/en-us/graph/api/teamworkhostedcontent-get?view=graph-rest-beta) | [teamworkHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/teamworkhostedcontent?view=graph-rest-beta) | Get hosted content \(and its bytes\) for an icon. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | The unique ID of the app icon. |
| webUrl | string | The web URL that can be used for downloading the image. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| hostedContent | [teamworkHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/teamworkhostedcontent?view=graph-rest-beta) | The contents of the app icon if the icon is hosted within the Teams infrastructure. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string",
  "webUrl": "string"
}
```

## Related content

- [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-beta)
- [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-beta)
