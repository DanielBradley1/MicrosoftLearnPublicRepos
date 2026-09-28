<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/jointransformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# joinTransformation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Creates a new value by joining two attributes. Optionally, you can use a separator between the two attributes.

Inherits from [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| input | [transformationAttribute](https://learn.microsoft.com/en-us/graph/api/resources/transformationattribute?view=graph-rest-beta) | The input attribute that provides the source for the transformation. This parameter is required if it's the first or only transformation in the list of transformations to be applied. Subsequent transformations use the output of the prior transformation as input. Inherited from [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta). |
| input2 | [transformationAttribute](https://learn.microsoft.com/en-us/graph/api/resources/transformationattribute?view=graph-rest-beta) | The second input used in the join operation. |
| separator | String | The separator value to be used. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.joinTransformation",
  "input": {
    "@odata.type": "microsoft.graph.transformationAttribute"
  },
  "input2": {
    "@odata.type": "microsoft.graph.transformationAttribute"
  },
  "separator": "String"
}
```
