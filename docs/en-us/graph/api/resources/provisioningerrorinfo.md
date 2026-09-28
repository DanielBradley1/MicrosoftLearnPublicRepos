<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/provisioningerrorinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# provisioningErrorInfo resource type

Namespace: microsoft.graph

Describes the status of the provisioning event and the associated errors. This object is configured in the **errorInformation** property of [provisioningStatusInfo](https://learn.microsoft.com/en-us/graph/api/resources/provisioningstatusinfo?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalDetails | String | Additional details if there's error. |
| errorCategory | provisioningStatusErrorCategory | Categorizes the error code. Possible values are `failure`, `nonServiceFailure`, `success`, `unknownFutureValue` |
| errorCode | String | Unique error code if any occurred. [Learn more](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/concept-provisioning-logs#error-codes) |
| reason | String | Summarizes the status and describes why the status happened. |
| recommendedAction | String | Provides the resolution for the corresponding error. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "additionalDetails": "String",
  "errorCategory": "String",
  "errorCode": "String",
  "reason": "String",
  "recommendedAction": "String"
}
```
