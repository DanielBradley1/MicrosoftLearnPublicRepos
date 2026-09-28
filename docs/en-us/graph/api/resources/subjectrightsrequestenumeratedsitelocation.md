<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequestenumeratedsitelocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# subjectRightsRequestEnumeratedSiteLocation resource type

Namespace: microsoft.graph

Represents the properties for a subject rights request that defines specific sites \(SharePoint sites, OneDrive for Business sites, and Microsoft Teams channels\) as a search location.

Inherits from [subjectRightsRequestSiteLocation](https://learn.microsoft.com/en-us/graph/api/resources/subjectrightsrequestsitelocation?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| urls | String collection | Collection of site URLs that should be included. Includes the URL of each site, for example, `https://www.contoso.com/site1`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.subjectRightsRequestEnumeratedSiteLocation",
  "urls": ["String"]
}
```
