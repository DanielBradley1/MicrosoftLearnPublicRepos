<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ifnotemptytransformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# ifNotEmptyTransformation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the output of a transformation if the input is not null or empty.

Inherits from [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| input | [transformationAttribute](https://learn.microsoft.com/en-us/graph/api/resources/transformationattribute?view=graph-rest-beta) | The input attribute that provides the source for the transformation. This parameter is required if it's the first or only transformation in the list of transformations to be applied. Subsequent transformations use the output of the prior transformation as input. Inherited from [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta). |
| output | [transformationAttribute](https://learn.microsoft.com/en-us/graph/api/resources/transformationattribute?view=graph-rest-beta) | The output attribute used, based on the condition applied in this transformation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ifNotEmptyTransformation",
  "input": {
    "@odata.type": "microsoft.graph.transformationAttribute"
  },
  "output": {
    "@odata.type": "microsoft.graph.transformationAttribute"
  }
}
```
