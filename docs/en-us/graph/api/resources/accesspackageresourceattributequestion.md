<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattributequestion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageResourceAttributeQuestion resource type

Namespace: microsoft.graph

Resource that defines the [question](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0) provided to an end user, for the purpose of obtaining an attribute value to be passed to the end system or the request approver.

This type inherits from [accessPackageResourceAttributeSource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattributesource?view=graph-rest-1.0) and is used in the **attributeSource** property of an [accessPackageResourceAttribute](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattribute?view=graph-rest-1.0).

The only property is **question**, which could be an [accessPackageTextInputQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagetextinputquestion?view=graph-rest-1.0) or a [accessPackageMultipleChoiceQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagemultiplechoicequestion?view=graph-rest-1.0) object type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| question | [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0) | The question asked in order to get the value of the attribute. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageResourceAttributeQuestion",
  "question": {
    "@odata.type": "microsoft.graph.accessPackageQuestion"
  }
}
```
