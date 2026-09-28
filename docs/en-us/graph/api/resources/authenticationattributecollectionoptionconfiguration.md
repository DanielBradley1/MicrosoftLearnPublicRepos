<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationattributecollectionoptionconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# authenticationAttributeCollectionOptionConfiguration resource type

Namespace: microsoft.graph

Represents the option values for certain input types, such as radio buttons, on an attribute collection page that is part of a self-service user flow for external identities.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| label | String | The label of the option that will be displayed to user, unless overridden. |
| value | String | The value of the option that will be stored. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationAttributeCollectionOptionConfiguration",
  "label": "String",
  "value": "String"
}
```
