<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-mediacontentratingunitedkingdom?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# mediaContentRatingUnitedKingdom resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| movieRating | [ratingUnitedKingdomMoviesType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingunitedkingdommoviestype?view=graph-rest-1.0) | Movies rating selected for United Kingdom. The possible values are: `allAllowed`, `allBlocked`, `general`, `universalChildren`, `parentalGuidance`, `agesAbove12Video`, `agesAbove12Cinema`, `agesAbove15`, `adults`. |
| tvRating | [ratingUnitedKingdomTelevisionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingunitedkingdomtelevisiontype?view=graph-rest-1.0) | TV rating selected for United Kingdom. The possible values are: `allAllowed`, `allBlocked`, `caution`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mediaContentRatingUnitedKingdom",
  "movieRating": "String",
  "tvRating": "String"
}
```
