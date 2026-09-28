<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/regexreplacetransformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# regexReplaceTransformation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Creates a new value by performing a regex replacement on the input.

Inherits from [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalAttributes | [sourcedAttribute](https://learn.microsoft.com/en-us/graph/api/resources/sourcedattribute?view=graph-rest-beta) collection | Additional attributes that can be referenced within the replacement string. |
| input | [transformationAttribute](https://learn.microsoft.com/en-us/graph/api/resources/transformationattribute?view=graph-rest-beta) | Provides the source for the transformation. This parameter is required if it's the first or only transformation in the list of transformations to be applied. Subsequent transformations use the output of the prior transformation as input. Inherited from [customClaimTransformation](https://learn.microsoft.com/en-us/graph/api/resources/customclaimtransformation?view=graph-rest-beta). |
| regex | String | The regular expression to be applied on the input directory attribute or constant. |
| replacement | String | The transformation output replacement pattern with regular expression output group and input parameter group reference. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.regexReplaceTransformation",
  "input": {
    "@odata.type": "microsoft.graph.transformationAttribute"
  },
  "regex": "String",
  "replacement": "String",
  "additionalAttributes": [
    {
      "@odata.type": "microsoft.graph.sourcedAttribute"
    }
  ]
}
```
