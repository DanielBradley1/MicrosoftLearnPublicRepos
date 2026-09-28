<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcalloutdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# accessPackageAssignmentRequestCalloutData resource type

Namespace: microsoft.graph

Represents the data sent to Azure Logic Apps as part of a [custom extension callout request](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutrequest?view=graph-rest-1.0) when a custom extension in a catalog gets used as part of an access package assignment request.

Inherits from [customExtensionData](https://learn.microsoft.com/en-us/graph/api/resources/customextensiondata?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessPackageAssignmentRequestId | String | The request ID of the access package assignment. |
| answers | [accessPackageAnswer](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageanswer?view=graph-rest-1.0) collection | The requestor's provided answer to an access package question. |
| callbackConfiguration | [customExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncallbackconfiguration?view=graph-rest-1.0) | The timeout duration for callback. |
| callbackUriPath | String | The URL where the reply to the call out goes. |
| customExtensionStageInstanceId | String | Unique identifier of the callout to the custom extension. |
| requestType | accessPackageRequestType | The type of the request. The possible values are: `notSpecified`, `userAdd`, `userUpdate`, `userRemove`, `adminAdd`, `adminUpdate`, `adminRemove`, `systemAdd`, `systemUpdate`, `systemRemove`, `onBehalfAdd`, `unknownFutureValue`. |
| stage | String | Indicates the stage at which the custom callout extension is executed. |
| state | accessPackageRequestState | The state in which the callout extension data is in. The possible values are: `submitted`, `pendingApproval`, `delivering`, `delivered`, `deliveryFailed`, `denied`, `scheduled`, `canceled`, `partiallyDelivered`, `unknownFutureValue`. |
| status | String | The status of the callout request. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessPackage | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) | The access package where the custom extension call out data to the Azure Logic App is being sent. |
| accessPackageCatalog | [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) | The catalog that contains the custom extension. |
| assignment | [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) | The specific assignment of the access package. |
| requestor | [accessPackageSubject](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesubject?view=graph-rest-1.0) | The user requesting the access package assignment. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentRequestCalloutData",
  "accessPackageAssignmentRequestId": "String",
  "callbackUriPath": "String",
  "customExtensionStageInstanceId": "String",
  "stage": "String",
  "requestType": "String",
  "answers": [
    {
      "@odata.type": "microsoft.graph.accessPackageAnswerString"
    }
  ],
  "state": "String",
  "status": "String",
  "callbackConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionCallbackConfiguration"
  }
}
```
