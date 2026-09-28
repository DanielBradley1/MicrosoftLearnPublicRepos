<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageAnswer resource type

Namespace: microsoft.graph

Represents the answer a requestor provides to an [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0). The actual answer will be a subtype of this complex type, either [accessPackageAnswerString](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswerstring?view=graph-rest-1.0) or [accessPackageAnswerChoice](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswerchoice?view=graph-rest-1.0). These answers will be stored on an [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0) object.

In entitlement management, this object is configured in the following properties and relationships:

- **answers** property of [accessPackageAssignmentRequest](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-1.0)
- **answers** property of [accessPackageAssignmentRequestCalloutData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcalloutdata?view=graph-rest-1.0)
- **existingAnswers** property of [accessPackageAssignmentRequestRequirements](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestrequirements?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| answeredQuestion | [accessPackageQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagequestion?view=graph-rest-1.0) | The question the answer is for. |
| displayValue | String | The localized display value shown to the requestor and approvers. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAnswer",
  "displayValue": "String",
  "answeredQuestion": {
    "@odata.type": "microsoft.graph.accessPackageQuestion"
  }
}
```
