<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/transformationattribute?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# transformationAttribute resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an attribute used to support transformations.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attribute | [customClaimAttributeBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimattributebase?view=graph-rest-beta) | Attribute to be used as input for the transformation. |
| treatAsMultiValue | Boolean | This flag is only relevant in the case where the attribute is multivalued. By default, transformations are only applied to the first element in a multi-valued claim, however setting this flag to `true` ensures the transformation is applied to all values, resulting in a multivalued output. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.transformationAttribute",
  "attribute": {
    "@odata.type": "microsoft.graph.customClaimAttributeBase"
  },
  "treatAsMultiValue": "Boolean"
}
```
