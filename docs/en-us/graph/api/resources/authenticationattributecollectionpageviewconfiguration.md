<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationattributecollectionpageviewconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-07 -->

# authenticationAttributeCollectionPageViewConfiguration resource type

Namespace: microsoft.graph

Represents the display of the attribute collection page that is part of a self-service user flow for external identities.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description of the page. |
| inputs | [authenticationAttributeCollectionInputConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationattributecollectioninputconfiguration?view=graph-rest-1.0) collection | The display configuration of attributes being collected on the attribute collection page. You must specify all attributes that you want to retain, otherwise they're removed from the user flow. |
| title | String | The title of the attribute collection page. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationAttributeCollectionPageViewConfiguration",
  "title": "String",
  "description": "String",
  "inputs": [
    {
      "@odata.type": "microsoft.graph.authenticationAttributeCollectionInputConfiguration"
    }
  ]
}
```
