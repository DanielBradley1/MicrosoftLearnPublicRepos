<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customclaimconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# customClaimConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a claim configuration that details the conditions and sources of any custom claim. Typically, an attribute or a set of transforms should be provided to source the claim value. In the case where both are provided, the output of the transforms takes priority. If the transform results in no output then the attribute value is used.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attribute | [customClaimAttributeBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimattributebase?view=graph-rest-beta) | The attribute on which we source this property. |
| condition | [customClaimConditionBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimconditionbase?view=graph-rest-beta) | The condition, if any, associated with this configuration. |
| transformations | [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta) collection | An ordered list of transformations that are applied in sequence. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customClaimConfiguration",
  "condition": {
    "@odata.type": "microsoft.graph.customClaimConditionBase"
  },
  "attribute": {
    "@odata.type": "microsoft.graph.customClaimAttributeBase"
  },
  "transformations": [
    {
      "@odata.type": "microsoft.graph.containsTransformation"
    }
  ]
}
```
