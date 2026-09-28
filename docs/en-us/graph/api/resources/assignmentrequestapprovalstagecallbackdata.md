<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/assignmentrequestapprovalstagecallbackdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-02 -->

# assignmentRequestApprovalStageCallbackData resource type

Namespace: microsoft.graph

Access package assignment request workflow callback that defines a custom extension endpoint approval callback that is derived from [customextensiondata](https://learn.microsoft.com/en-us/graph/api/resources/customextensiondata?view=graph-rest-1.0).

Inherits from [accessPackageAssignmentRequestCallbackData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcallbackdata?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalStage | [accessPackageApprovalStage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageapprovalstage?view=graph-rest-1.0) | The stage in the approval decision. |
| customExtensionStageInstanceDetail | String | Details for the callback. Inherited from [accessPackageAssignmentRequestCallbackData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcallbackdata?view=graph-rest-1.0). |
| customExtensionStageInstanceId | String | Unique identifier of the callout to the custom extension. Inherited from [accessPackageAssignmentRequestCallbackData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcallbackdata?view=graph-rest-1.0). |
| stage | accessPackageCustomExtensionStage | Indicates the stage at which the custom callout extension is executed. Inherited from [accessPackageAssignmentRequestCallbackData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcallbackdata?view=graph-rest-1.0). The possible values are: `assignmentRequestCreated`, `assignmentRequestApproved`, `assignmentRequestGranted`, `assignmentRequestRemoved`, `assignmentFourteenDaysBeforeExpiration`, `assignmentOneDayBeforeExpiration`, `unknownFutureValue`. |
| state | String | Allows the extension to be able to deny or cancel the request submitted by the requestor. The supported values are `Denied` and `Canceled`. This property can only be set for an `assignmentRequestCreated` stage. Inherited from [accessPackageAssignmentRequestCallbackData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcallbackdata?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.assignmentRequestApprovalStageCallbackData",
  "stage": "String",
  "customExtensionStageInstanceId": "String",
  "customExtensionStageInstanceDetail": "String",
  "state": "String",
  "approvalStage": {
    "@odata.type": "microsoft.graph.accessPackageApprovalStage"
  }
}
```
