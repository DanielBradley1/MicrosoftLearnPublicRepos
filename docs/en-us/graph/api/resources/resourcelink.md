<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resourcelink?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# resourceLink resource type

Namespace: microsoft.graph

Represents external links that should be associated with a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) in Places, such as a dining menu or a link to other services.

For more information on how to set up services in Places, see [Add services to buildings](https://learn.microsoft.com/en-us/microsoft-365/places/services-in-places).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| linkType | resourceLinkType | Type of link. The possible values are: `url`, `unknownFutureValue`. |
| name | String | The link text that is visible in the Places app. The maximum length is 200 characters. |
| value | String | The URL of the resource link. The maximum length is 200 characters. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.resourceLink",
  "linkType": "String",
  "name": "String",
  "value": "String"
}
```
