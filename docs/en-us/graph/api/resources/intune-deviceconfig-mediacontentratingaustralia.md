<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-mediacontentratingaustralia?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# mediaContentRatingAustralia resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| movieRating | [ratingAustraliaMoviesType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingaustraliamoviestype?view=graph-rest-1.0) | Movies rating selected for Australia. The possible values are: `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `mature`, `agesAbove15`, `agesAbove18`. |
| tvRating | [ratingAustraliaTelevisionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingaustraliatelevisiontype?view=graph-rest-1.0) | TV rating selected for Australia. The possible values are: `allAllowed`, `allBlocked`, `preschoolers`, `children`, `general`, `parentalGuidance`, `mature`, `agesAbove15`, `agesAbove15AdultViolence`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mediaContentRatingAustralia",
  "movieRating": "String",
  "tvRating": "String"
}
```
