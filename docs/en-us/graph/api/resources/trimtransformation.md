<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trimtransformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# trimTransformation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Eliminates leading and trailing characters that match the provided input.

Inherits from [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| input | [transformationAttribute](https://learn.microsoft.com/en-us/graph/api/resources/transformationattribute?view=graph-rest-beta) | Attribute that provides the source for the transformation. This parameter is required if it is the first or only transformation in the list of transformations to be applied. Subsequent transformations use the output of the prior transformation as input. Inherited from [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta). |
| type | transformationTrimType | The type of trim transformation to apply. The possible values are: `leading`, `trailing`, `leadingAndTrailing`, `unknownFutureValue`. |
| value | String | The value to be used as part of the transformation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trimTransformation",
  "input": {
    "@odata.type": "microsoft.graph.transformationAttribute"
  },
  "type": "String",
  "value": "String"
}
```
