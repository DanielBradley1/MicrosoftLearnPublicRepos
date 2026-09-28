<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/simulationautomation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# simulationAutomation resource type

Namespace: microsoft.graph

Represents simulation automation created to run on a tenant.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List simulationAutomations](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-simulationautomations?view=graph-rest-1.0) | [simulationAutomation](https://learn.microsoft.com/en-us/graph/api/resources/simulationautomation?view=graph-rest-1.0) collection | Get a list of attack simulation automations for a tenant. |
| [Get simulationAutomation](https://learn.microsoft.com/en-us/graph/api/simulationautomation-get?view=graph-rest-1.0) | [simulationAutomation](https://learn.microsoft.com/en-us/graph/api/resources/simulationautomation?view=graph-rest-1.0) | Get an attack simulation automation for a tenant. |
| [List runs](https://learn.microsoft.com/en-us/graph/api/simulationautomation-list-runs?view=graph-rest-1.0) | [simulationAutomationRun](https://learn.microsoft.com/en-us/graph/api/resources/simulationautomationrun?view=graph-rest-1.0) collection | Get a list of the attack simulation automation runs for a tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who created the attack simulation automation. |
| createdDateTime | DateTimeOffset | Date and time when the attack simulation automation was created. |
| description | String | Description of the attack simulation automation. |
| displayName | String | Display name of the attack simulation automation. Supports `$filter` and `$orderby`. |
| id | String | Unique identifier for the attack simulation automation. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-1.0) | Identity of the user who most recently modified the attack simulation automation. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the attack simulation automation was most recently modified. |
| lastRunDateTime | DateTimeOffset | Date and time of the latest run of the attack simulation automation. |
| nextRunDateTime | DateTimeOffset | Date and time of the upcoming run of the attack simulation automation. |
| status | [simulationAutomationStatus](#simulationautomationstatus-values) | Status of the attack simulation automation. Supports `$filter` and `$orderby`. The possible values are: `unknown`, `draft`, `notRunning`, `running`, `completed`, `unknownFutureValue`. |

### simulationAutomationStatus values

| Member | Description |
| :--- | :--- |
| unknown | The status of the simulation automation isn't defined. |
| draft | The simulation automation is in draft mode. |
| notRunning | The simulation automation isn't running. |
| running | The simulation automation is running. |
| completed | The simulation automation has completed. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| runs | [simulationAutomationRun](https://learn.microsoft.com/en-us/graph/api/resources/simulationautomationrun?view=graph-rest-1.0) collection | A collection of simulation automation runs. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.simulationAutomation",
  "createdBy": {
    "@odata.type": "microsoft.graph.emailIdentity"
  },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.emailIdentity"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "lastRunDateTime": "String (timestamp)",
  "nextRunDateTime": "String (timestamp)",
  "status": "String"
}
```
