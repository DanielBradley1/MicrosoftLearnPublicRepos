<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/offboardingdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-10 -->

# offboardingDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information about an offboarding operation, including counts of protection units that were successfully offboarded, failed, or cancelled, along with the timing and status of the offboarding process.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cancelledCount | Int32 | The number of protection units whose offboarding was cancelled during the operation. |
| failedCount | Int32 | The number of protection units that failed to be offboarded during the operation. |
| offboardedCount | Int32 | The number of protection units that were successfully offboarded during the operation. |
| offboardEndDateTime | DateTimeOffset | The date and time when the offboarding operation ended. |
| offboardingStatus | String | The current status of the offboarding operation. |
| offboardStartDateTime | DateTimeOffset | The date and time when the offboarding operation started. |
| totalRequestedCount | Int32 | The total number of protection units that were requested to be offboarded in this operation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.offboardingDetails",
  "totalRequestedCount": "Integer",
  "offboardedCount": "Integer",
  "failedCount": "Integer",
  "cancelledCount": "Integer",
  "offboardStartDateTime": "String (timestamp)",
  "offboardEndDateTime": "String (timestamp)",
  "offboardingStatus": "String"
}
```
