<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-mediacontentratingjapan?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# mediaContentRatingJapan resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| movieRating | [ratingJapanMoviesType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingjapanmoviestype?view=graph-rest-1.0) | Movies rating selected for Japan. The possible values are: `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `agesAbove15`, `agesAbove18`. |
| tvRating | [ratingJapanTelevisionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingjapantelevisiontype?view=graph-rest-1.0) | TV rating selected for Japan. The possible values are: `allAllowed`, `allBlocked`, `explicitAllowed`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mediaContentRatingJapan",
  "movieRating": "String",
  "tvRating": "String"
}
```
