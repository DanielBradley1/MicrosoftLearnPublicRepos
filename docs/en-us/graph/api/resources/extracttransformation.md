<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/extracttransformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# extractTransformation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Returns the substring after, between or before it matches the specified value.

Inherits from [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| input | [transformationAttribute](https://learn.microsoft.com/en-us/graph/api/resources/transformationattribute?view=graph-rest-beta) | The input attribute that provides the source for the transformation. This parameter is required if it's the first or only transformation in the list of transformations to be applied. Subsequent transformations use the output of the prior transformation as input. Inherited from [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta). |
| type | String | The type of extract transformation to apply. |
| value | String | The value to be used as part of the transformation. |
| value2 | String | An optional secondary value to be used when dealing with between extract operations. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.extractTransformation",
  "input": {
    "@odata.type": "microsoft.graph.transformationAttribute"
  },
  "type": "String",
  "value": "String",
  "value2": "String"
}
```
