<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamfunsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# teamFunSettings resource type

Namespace: microsoft.graph

Settings to configure use of Giphy, memes, and stickers in the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowCustomMemes | Boolean | If set to true, enables users to include custom memes. |
| allowGiphy | Boolean | If set to true, enables Giphy use. |
| allowStickersAndMemes | Boolean | If set to true, enables users to include stickers and memes. |
| giphyContentRating | String \(enum\) | Giphy content rating. The possible values are: `moderate`, `strict`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowGiphy": true,
  "giphyContentRating": "strict",
  "allowStickersAndMemes": true,
  "allowCustomMemes": true
}
```
