<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-mediacontentratingcanada?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# mediaContentRatingCanada resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| movieRating | [ratingCanadaMoviesType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingcanadamoviestype?view=graph-rest-1.0) | Movies rating selected for Canada. The possible values are: `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `agesAbove14`, `agesAbove18`, `restricted`. |
| tvRating | [ratingCanadaTelevisionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingcanadatelevisiontype?view=graph-rest-1.0) | TV rating selected for Canada. The possible values are: `allAllowed`, `allBlocked`, `children`, `childrenAbove8`, `general`, `parentalGuidance`, `agesAbove14`, `agesAbove18`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mediaContentRatingCanada",
  "movieRating": "String",
  "tvRating": "String"
}
```
