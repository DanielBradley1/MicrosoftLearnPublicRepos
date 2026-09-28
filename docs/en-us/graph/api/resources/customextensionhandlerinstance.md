<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensionhandlerinstance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# customExtensionHandlerInstance resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Used to record the status of [custom workflow extension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) instance being run on an [access package assignment request](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequest?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customExtensionId | String | Identifier of the [customAccessPackageWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/customaccesspackageworkflowextension?view=graph-rest-beta) triggered at this instance. |
| externalCorrelationId | String | The unique run ID for the logic app. |
| stage | accessPackageCustomExtensionStage | Indicates the stage of the request workflow when the access package custom extension runs. The possible values are: `assignmentRequestCreated`, `assignmentRequestApproved`, `assignmentRequestGranted`, `assignmentRequestRemoved`, `assignmentFourteenDaysBeforeExpiration`, `assignmentOneDayBeforeExpiration`, `unknownFutureValue`. |
| status | accessPackageCustomExtensionHandlerStatus | Status of the request to run the access package custom extension workflow that is associated with the logic app. The possible values are: `requestSent`, `requestReceived`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json

{
  "@odata.type": "#microsoft.graph.customExtensionHandlerInstance",
  "stage": "String",
  "customExtensionId": "String",
  "externalCorrelationId": "String",
  "status": "String"
}
```
