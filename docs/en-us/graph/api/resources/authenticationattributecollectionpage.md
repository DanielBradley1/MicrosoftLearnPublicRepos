<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationattributecollectionpage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# authenticationAttributeCollectionPage resource type

Namespace: microsoft.graph

Represents the attribute collection page that is part of a self-service user flow for external identities.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| views | [authenticationAttributeCollectionPageViewConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationattributecollectionpageviewconfiguration?view=graph-rest-1.0) collection | A collection of displays of the attribute collection page. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationAttributeCollectionPage",
  "views": [
    {
      "@odata.type": "microsoft.graph.authenticationAttributeCollectionPageViewConfiguration"
    }
  ]
}
```
