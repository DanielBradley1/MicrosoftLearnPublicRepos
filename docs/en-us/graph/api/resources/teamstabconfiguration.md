<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamstabconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# teamsTabConfiguration resource type \(Open Type\)

Namespace: microsoft.graph

The settings that determine the content of a [tab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0). When a tab is interactively configured, this information is set by the tab provider application. In addition to the properties below, some tab provider applications specify additional custom properties.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| contentUrl | string | Url used for rendering tab contents in Teams. Required. |
| entityId | string | Identifier for the entity hosted by the tab provider. |
| removeUrl | string | Url called by Teams client when a Tab is removed using the Teams Client. |
| websiteUrl | string | Url for showing tab contents outside of Teams. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
   "entityId": "string",
   "contentUrl": "string (HTTPS Url)",
   "websiteUrl": "string (HTTPS Url)",
   "removeUrl": "string (HTTPS Url)"  
}
```
