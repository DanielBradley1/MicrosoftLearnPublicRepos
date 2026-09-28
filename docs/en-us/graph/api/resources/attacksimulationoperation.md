<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# attackSimulationOperation resource type

Namespace: microsoft.graph

Represents the status of a long-running attack simulation training operation.

Inherits from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/attacksimulationoperation-get?view=graph-rest-1.0) | [attackSimulationOperation](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationoperation?view=graph-rest-1.0) | Get an attack simulation operation to track a long-running operation request for a tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Operation created date time. The timestamp represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |
| id | String | The unique identifier for the operation. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastActionDateTime | DateTimeOffset | The time of the last action in the operation. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |
| percentageCompleted | Int32 | Percentage of completion of the respective operation. |
| resourceLocation | String | URI of the resource location. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |
| status | longRunningOperationStatus | Operation status. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |
| statusDetail | String | Status detail of the operation. Inherited from [longRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/longrunningoperation?view=graph-rest-1.0). |
| tenantId | String | Tenant identifier. |
| type | [attackSimulationOperationType](#attacksimulationoperationtype-values) | The attack simulation operation type. The possible values are: `createSimulation`, `updateSimulation`, `unknownFutureValue`. |

### attackSimulationOperationType values

| Member | Description |
| :--- | :--- |
| createSimulation | The simulation creation operation. |
| updateSimulation | The simulation update operation. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.attackSimulationOperation",
    "createdDateTime": "String (timestamp)",
    "id": "String (identifier)",
    "lastActionDateTime": "String (timestamp)",
    "percentageCompleted": "Int32",
    "resourceLocation": "String",
    "status": "String",
    "statusDetail": "String",
    "tenantId": "String",
    "type": "String"
}
```

## Related content

- [Simulate a phishing attack](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training?view=o365-worldwide&preserve-view=true)
- [Get started using attack simulation training](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training-get-started?view=o365-worldwide&preserve-view=true#simulations).
