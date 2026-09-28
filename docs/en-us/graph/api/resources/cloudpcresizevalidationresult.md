<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcresizevalidationresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# cloudPcResizeValidationResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the validation result of a single resized Cloud PC during the bulk-resize action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudPcId | String | The [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta) ID that corresponds to its unique identifier. |
| validationResult | [cloudPcResizeValidationCode](#cloudpcresizevalidationcode-values) | Describes a list of the validation result for the Cloud PC resize action. The possible values are: `success`, `cloudPcNotFound`, `operationCnflict`, `operationNotSupported`, `targetLicenseHasAssigned`, `internalServerError`, and `unknownFutureValue`. |

### cloudPcResizeValidationCode values

| Member | Description |
| :--- | :--- |
| success | Indicates that the resize validation was successful. |
| cloudPcNotFound | Indicates that the Cloud PC wasn't found. |
| operationConflict | Indicates that resize action has a conflict with another action. |
| operationNotSupported | Indicates that the resize action isn't supported for the Cloud PC. |
| targetLicenseHasAssigned | Indicates that the target license has already been assigned to the user. |
| internalServerError | Indicates that the validation failed with an internal server error. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{ 
  "cloudPcId": "30d0e128-de93-41dc-89ec-33d84bb662a0",
  "validationResult": "success" 
}
```
