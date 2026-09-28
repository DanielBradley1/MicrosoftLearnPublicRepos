<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-mediacontentratingfrance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# mediaContentRatingFrance resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| movieRating | [ratingFranceMoviesType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingfrancemoviestype?view=graph-rest-1.0) | Movies rating selected for France. The possible values are: `allAllowed`, `allBlocked`, `agesAbove10`, `agesAbove12`, `agesAbove16`, `agesAbove18`. |
| tvRating | [ratingFranceTelevisionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingfrancetelevisiontype?view=graph-rest-1.0) | TV rating selected for France. The possible values are: `allAllowed`, `allBlocked`, `agesAbove10`, `agesAbove12`, `agesAbove16`, `agesAbove18`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mediaContentRatingFrance",
  "movieRating": "String",
  "tvRating": "String"
}
```
