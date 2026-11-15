<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/investigationinput?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# investigationInput resource type

Namespace: microsoft.graph

Represents an external resource identifier or keyword supplied to an agentic session. Inputs are shared session context, not a record of the exact input consumed by each agent run. Supply inputs only inline when creating the session; subsequent input writes aren't supported.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List inputs](https://learn.microsoft.com/en-us/graph/api/investigationsession-list-inputs?view=graph-rest-beta) | [investigationInput](https://learn.microsoft.com/en-us/graph/api/resources/investigationinput?view=graph-rest-beta) collection | Get the session inputs. |
| [Get](https://learn.microsoft.com/en-us/graph/api/investigationinput-get?view=graph-rest-beta) | [investigationInput](https://learn.microsoft.com/en-us/graph/api/resources/investigationinput?view=graph-rest-beta) | Read an input. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name populated by the service when available. Read-only. |
| id | String | The stable, service-generated input identifier, unique within its containing session. Read-only. Don't supply it on deep insert. |
| kind | investigationInputType | The input kind. Required when creating a session and immutable afterward. The possible values are: `defenderIncidentId`, `defenderAlertId`, `defenderThreatIntelligenceId`, `azureSubscriptionId`, `azureIdentityId`, `keyword`, `unknownFutureValue`. The selected playbook must accept the kind. Don't supply `unknownFutureValue`. |
| value | String | The type-specific resource identifier or keyword text. Required when creating a session and immutable afterward. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.investigationInput",
  "id": "String (identifier)",
  "value": "String",
  "kind": "String",
  "displayName": "String"
}
```
