<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-mediacontentratingireland?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# mediaContentRatingIreland resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| movieRating | [ratingIrelandMoviesType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingirelandmoviestype?view=graph-rest-1.0) | Movies rating selected for Ireland. The possible values are: `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `agesAbove12`, `agesAbove15`, `agesAbove16`, `adults`. |
| tvRating | [ratingIrelandTelevisionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingirelandtelevisiontype?view=graph-rest-1.0) | TV rating selected for Ireland. The possible values are: `allAllowed`, `allBlocked`, `general`, `children`, `youngAdults`, `parentalSupervision`, `mature`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mediaContentRatingIreland",
  "movieRating": "String",
  "tvRating": "String"
}
```
