<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumberlongrunningoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# telephoneNumberLongRunningOperation resource type

Namespace: microsoft.graph.teamsAdministration

Represents the operations available for getting telephone number asynchronous operation details.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamsadministration-telephonenumberlongrunningoperation-get?view=graph-rest-1.0) | [microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumberlongrunningoperation?view=graph-rest-1.0) | Read the properties and relationships of [microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumberlongrunningoperation?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | String | Date and time when the asynchronous operation was created. |
| id | String | Operation identifier found as a response to asynchronous action. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| numbers | [microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperationDetails](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumberlongrunningoperationdetails?view=graph-rest-1.0) collection | Asynchronous operation details. |
| status | longRunningOperationStatus | Status of the operation. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `skipped, and `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperation",
  "id": "String (identifier)",
  "createdDateTime": "String",
  "status": "String",
  "numbers": [
    {
      "@odata.type": "microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperationDetails"
    }
  ]
}
```
