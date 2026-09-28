<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentcalloutdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# accessPackageAssignmentCalloutData resource type

Namespace: microsoft.graph

Represents the data sent to Azure Logic Apps as part of a [custom extension callout request](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutrequest?view=graph-rest-1.0) when a custom extension in a catalog gets used as part of an access package assignment.

Inherits from [customExtensionData](https://learn.microsoft.com/en-us/graph/api/resources/customextensiondata?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessPackageAssignmentRequestId | String | The request ID of the access package assignment. |
| callbackConfiguration | [customExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncallbackconfiguration?view=graph-rest-1.0) | The callback configuration for a custom extension. |
| customExtensionStageInstanceId | String | Unique identifier of the callout to the custom extension. |
| stage | String | Indicates the stage of the access package assignment request workflow when the access package custom extension runs. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessPackage | [accessPackage](https://learn.microsoft.com/en-us/graph/api/resources/accesspackage?view=graph-rest-1.0) | The access package where the custom extension call out data to the Azure Logic App is being sent. |
| accessPackageCatalog | [accessPackageCatalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) | The catalog that contains the custom extension. |
| assignment | [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-1.0) | The specific assignment of the access package. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentCalloutData",
  "accessPackageAssignmentRequestId": "String",
  "customExtensionStageInstanceId": "String",
  "stage": "String",
  "callbackConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionCallbackConfiguration"
  }
}
```
