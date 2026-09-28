<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventpresenterdetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# virtualEventPresenterDetails resource type

Namespace: microsoft.graph

Represents detailed information about a virtual event presenter.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bio | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Bio of the presenter. |
| company | String | The presenter's company name. |
| jobTitle | String | The presenter's job title. |
| linkedInProfileWebUrl | String | The presenter's LinkedIn profile URL. |
| personalSiteWebUrl | String | The presenter's personal website URL. |
| photo | Stream | The content stream of the presenter's photo. |
| twitterProfileWebUrl | String | The presenter's Twitter profile URL. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventPresenterDetails",
  "bio": {"@odata.type": "microsoft.graph.itemBody"},
  "company": "String",
  "jobTitle": "String",
  "linkedInProfileWebUrl": "String",
  "personalSiteWebUrl": "String",
  "photo": "Stream",
  "twitterProfileWebUrl": "String"
}
```
