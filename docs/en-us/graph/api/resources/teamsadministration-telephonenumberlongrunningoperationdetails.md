<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumberlongrunningoperationdetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# telephoneNumberLongRunningOperationDetails resource type

Namespace: microsoft.graph.teamsAdministration

Represents the telephone number asynchronous operation details.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resourceLocation | String | Location of the asynchronous operation. It includes the operation identifier. |
| status | longRunningOperationStatus | status of the asynchronous operation. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. |
| statusDetail | String | Indicates the asynchronous operation details. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperationDetails",
  "resourceLocation": "String",
  "status": "String",
  "statusDetail": "String"
}
```
