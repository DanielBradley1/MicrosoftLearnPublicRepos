<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-mediacontentratinggermany?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# mediaContentRatingGermany resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| movieRating | [ratingGermanyMoviesType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratinggermanymoviestype?view=graph-rest-1.0) | Movies rating selected for Germany. The possible values are: `allAllowed`, `allBlocked`, `general`, `agesAbove6`, `agesAbove12`, `agesAbove16`, `adults`. |
| tvRating | [ratingGermanyTelevisionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratinggermanytelevisiontype?view=graph-rest-1.0) | TV rating selected for Germany. The possible values are: `allAllowed`, `allBlocked`, `general`, `agesAbove6`, `agesAbove12`, `agesAbove16`, `adults`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mediaContentRatingGermany",
  "movieRating": "String",
  "tvRating": "String"
}
```
