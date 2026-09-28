<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-mediacontentratingunitedstates?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# mediaContentRatingUnitedStates resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| movieRating | [ratingUnitedStatesMoviesType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingunitedstatesmoviestype?view=graph-rest-1.0) | Movies rating selected for United States. The possible values are: `allAllowed`, `allBlocked`, `general`, `parentalGuidance`, `parentalGuidance13`, `restricted`, `adults`. |
| tvRating | [ratingUnitedStatesTelevisionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ratingunitedstatestelevisiontype?view=graph-rest-1.0) | TV rating selected for United States. The possible values are: `allAllowed`, `allBlocked`, `childrenAll`, `childrenAbove7`, `general`, `parentalGuidance`, `childrenAbove14`, `adults`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mediaContentRatingUnitedStates",
  "movieRating": "String",
  "tvRating": "String"
}
```
