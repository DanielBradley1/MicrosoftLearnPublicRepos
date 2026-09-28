<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-mediacontentratingnewzealand?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# mediaContentRatingNewZealand resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| movieRating | [ratingNewZealandMoviesType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingnewzealandmoviestype?view=graph-rest-1.0) | Movies rating selected for New Zealand. The possible values are: `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `mature`, `agesAbove13`, `agesAbove15`, `agesAbove16`, `agesAbove18`, `restricted`, `agesAbove16Restricted`. |
| tvRating | [ratingNewZealandTelevisionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingnewzealandtelevisiontype?view=graph-rest-1.0) | TV rating selected for New Zealand. The possible values are: `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `adults`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mediaContentRatingNewZealand",
  "movieRating": "String",
  "tvRating": "String"
}
```
