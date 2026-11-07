<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-03 -->

# detectionRule resource type

Namespace: microsoft.graph.security

Represents a custom detection rule written in **Advanced hunting** to automatically recognize security events when they occur, and to trigger alerts and response actions.

Custom detection rules let you proactively monitor various events and system states by using [advanced hunting](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-1.0) queries, including suspected breach activity and misconfigured endpoints. A custom detection rule automatically recognizes security events when they occur, and triggers alerts and response actions. You can set the rules to run at regular intervals, generating alerts and taking response actions whenever matches occur.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-rulesroot-list-detectionrules?view=graph-rest-1.0) | [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) collection | Get a list of the [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-rulesroot-post-detectionrules?view=graph-rest-1.0) | [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) | Create a new [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-detectionrule-get?view=graph-rest-1.0) | [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) | Read the properties and relationships of a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-detectionrule-update?view=graph-rest-1.0) | [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) | Update the properties of a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-rulesroot-delete-detectionrules?view=graph-rest-1.0) | None | Delete a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | Name of the user or application that created the rule. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `in`, `startsWith`, `endsWith`, `contains`\). |
| createdDateTime | DateTimeOffset | Timestamp of rule creation. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `le`, `ge`, `lt`, `gt`\) and `$orderby`. |
| description | String | A user-supplied description of the detection rule. Supports `$filter` \(`eq`, `ne`, `not`, `in`, `startsWith`, `endsWith`, `contains`\). |
| detectionAction | [microsoft.graph.security.detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-1.0) | The actions taken when a detection is made by this rule, including the alert that is created and any automated response actions. Supports `$filter` on the following nested **alertTemplate** properties:  <br><br><br><li>String: <strong>detectionAction/alertTemplate/title</strong>, <strong>detectionAction/alertTemplate/description</strong>, <strong>detectionAction/alertTemplate/recommendedActions</strong> — each supports <code>eq</code>, <code>ne</code>, <code>not</code>, <code>in</code>, <code>startsWith</code>, <code>endsWith</code>, <code>contains</code>.</li><br><br><li>Enum: <strong>detectionAction/alertTemplate/severity</strong> — supports <code>eq</code>, <code>ne</code>, <code>not</code>, <code>in</code>.</li> |
| displayName | String | The display name of the rule. Supports `$filter` \(`eq`, `ne`, `not`, `in`, `startsWith`, `endsWith`, `contains`\) and `$orderby`. |
| id | String | The client-provided unique identifier of the rule. Supports `$filter` \(`eq`, `ne`, `not`, `in`\) and `$orderby`. |
| lastModifiedBy | String | Name of the user or application that last updated the rule. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `in`, `startsWith`, `endsWith`, `contains`\). |
| lastModifiedDateTime | DateTimeOffset | Timestamp of when the rule was last updated. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `le`, `ge`, `lt`, `gt`\) and `$orderby`. |
| queryCondition | [microsoft.graph.security.queryCondition](https://learn.microsoft.com/en-us/graph/api/resources/security-querycondition?view=graph-rest-1.0) | The advanced hunting query that defines the detection logic of this rule. Supports `$filter` on **queryCondition/queryText** \(String\) with `eq`, `ne`, `not`, `in`, `startsWith`, `endsWith`, `contains`. |
| schedule | [microsoft.graph.security.ruleSchedule](https://learn.microsoft.com/en-us/graph/api/resources/security-ruleschedule?view=graph-rest-1.0) | The triggering schedule of this rule. Supports `$filter` on **schedule/frequency** \(Duration\) with `eq`, `ne`, `not`, `le`, `ge`, `lt`, `gt`. Supports `$orderby` on **schedule/frequency**. |
| status | microsoft.graph.security.detectionRuleStatus | The current run status of the rule. The possible values are: `enabled`, `disabled`, `autoDisabled`, `unknownFutureValue`. Supports `$filter` \(`eq`, `ne`, `not`, `in`\) and `$orderby`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.detectionRule",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "status": "String",
  "createdBy": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "queryCondition": {
    "@odata.type": "microsoft.graph.security.queryCondition"
  },
  "schedule": {
    "@odata.type": "microsoft.graph.security.ruleSchedule"
  },
  "detectionAction": {
    "@odata.type": "microsoft.graph.security.detectionAction"
  }
}
```
