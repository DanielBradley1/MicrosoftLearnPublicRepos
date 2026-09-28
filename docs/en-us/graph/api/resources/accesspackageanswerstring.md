<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswerstring?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageAnswerString resource type

Namespace: microsoft.graph

Indicates the string input answer to an [accessPackageTextInputQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagetextinputquestion?view=graph-rest-1.0). Stored on an [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0).

Inherits from [accessPackageAnswer](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswer?view=graph-rest-1.0).

In entitlement management, this subtype is used in the:

- **answers** property of [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0)
- **answers** property of [accessPackageAssignmentRequestCalloutData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcalloutdata?view=graph-rest-1.0)
- **existingAnswers** property of [accessPackageAssignmentRequestRequirements](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestrequirements?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| answeredQuestion | [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0) | The question the answer applies to. Inherited from [accessPackageAnswer](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswer?view=graph-rest-1.0). |
| displayValue | String | The localized display value shown to the requestor and approvers. Inherited from [accessPackageAnswer](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswer?view=graph-rest-1.0). |
| value | String | The value stored on the requestor's user profile, if this answer is configured to be stored as a specific attribute. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAnswerString",
  "displayValue": "String",
  "answeredQuestion": {
    "@odata.type": "microsoft.graph.accessPackageQuestion"
  },
  "value": "String"
}
```
