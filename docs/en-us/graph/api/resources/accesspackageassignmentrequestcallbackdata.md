<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcallbackdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# accessPackageAssignmentRequestCallbackData resource type

Namespace: microsoft.graph

Access package assignment request workflow calllback back that custom extension endpoint callback, derived from [customextensiondata](https://learn.microsoft.com/en-us/graph/api/resources/customextensiondata?view=graph-rest-1.0)

Inherits from [customExtensionData](https://learn.microsoft.com/en-us/graph/api/resources/customextensiondata?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customExtensionStageInstanceId | String | Unique identifier of the callout to the custom extension. |
| customExtensionStageInstanceDetail | String | Details for the callback. |
| stage | accessPackageCustomExtensionStage | Indicates the stage at which the custom callout extension is executed. The possible values are: `assignmentRequestCreated`, `assignmentRequestApproved`, `assignmentRequestGranted`, `assignmentRequestRemoved`, `assignmentFourteenDaysBeforeExpiration`, `assignmentOneDayBeforeExpiration`, `unknownFutureValue`. |
| state | accessPackageRequestState | Allow the extension to be able to deny or cancel the request submitted by the requestor. The supported values are `Denied` and `Canceled`. This property can only be set for an `assignmentRequestCreated` stage. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestCallbackData",
  "stage": "Microsoft.IGAELM.EC.FrontEnd.ExternalModel.accessPackageCustomExtensionStage",
  "customExtensionStageInstanceId": "String",
  "customExtensionStageInstanceDetail": "String",
  "state": "String"
}
```
