<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/statusdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# statusDetails resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The statusDetails API is deprecated and will stop returning data om December 31, 2021. Please use the new [provisioningStatusInfo](https://learn.microsoft.com/en-us/graph/api/resources/provisioningstatusinfo?view=graph-rest-beta) type.

Describes the status of the provisioning event and the associated errors. It's inherited from [statusBase](https://learn.microsoft.com/en-us/graph/api/resources/statusbase) and only used when status is set to `failure`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| status | statusBase | The possible values are: `success`, `warning`, `failure`, `skipped`, `unknownFutureValue`. Inherited from statusBase. |
| additionalDetails | String | Additional details if there is an error. |
| errorCategory | String | Categorizes the error code. Possible values are `Failure`, `NonServiceFailure`, `Success`. |
| errorCode | String | Unique error code if any occurred. [Learn more](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/concept-provisioning-logs#error-codes) |
| reason | String | Summarizes the status and describes why the status happened. |
| recommendedAction | String | Provides the resolution for the corresponding error. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "status": "failure",
  "additionalDetails": "String",
  "errorCategory": "String",
  "errorCode": "String",
  "reason": "String",
  "recommendedAction": "String"
}
```
