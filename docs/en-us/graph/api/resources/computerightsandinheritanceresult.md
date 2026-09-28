<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/computerightsandinheritanceresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# computeRightsAndInheritanceResult resource type

Namespace: microsoft.graph

Represents the result entity for a compute rights and inheritance operation.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| contentRights | [labelContentRight](https://learn.microsoft.com/en-us/graph/api/resources/labelcontentright?view=graph-rest-1.0) collection | A collection of content rights entities for the content. |
| inheritedLabel | [microsoft.graph.security.sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-1.0) | The sensitivity label that is inherited by the content based on the input labels and content formats. |
| sensitivityLabels | [microsoft.graph.security.sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-1.0) collection | A collection of sensitivity labels that are applicable to the content. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.computeRightsAndInheritanceResult"
}
```
