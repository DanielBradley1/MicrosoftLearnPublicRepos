<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# detectionRule resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a custom detection rule written in **Advanced hunting** to automatically recognize security events when they occur, and to trigger alerts and response actions.

Custom detection rules let you proactively monitor various events and system states by using [advanced hunting](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-beta) queries, including suspected breach activity and misconfigured endpoints. A custom detection rule automatically recognizes security events when they occur, and triggers alerts and response actions. You can set the rules to run at regular intervals, generating alerts and taking response actions whenever matches occur.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-rulesroot-list-detectionrules?view=graph-rest-beta) | [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) collection | Get a list of the [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-rulesroot-post-detectionrules?view=graph-rest-beta) | [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) | Create a new [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-detectionrule-get?view=graph-rest-beta) | [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) | Read the properties and relationships of a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-detectionrule-update?view=graph-rest-beta) | [microsoft.graph.security.detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) | Update the properties of a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-rulesroot-delete-detectionrules?view=graph-rest-beta) | None | Delete a [detectionRule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | Name of the user or application that created the rule. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `in`, `startsWith`, `endsWith`, `contains`\). |
| createdDateTime | DateTimeOffset | Timestamp of rule creation. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `le`, `ge`, `lt`, `gt`\) and `$orderby`. |
| description | String | A user-supplied description of the detection rule. Supports `$filter` \(`eq`, `ne`, `not`, `in`, `startsWith`, `endsWith`, `contains`\). |
| displayName | String | The display name of the rule. Supports `$filter` \(`eq`, `ne`, `not`, `in`, `startsWith`, `endsWith`, `contains`\) and `$orderby`. |
| id | String | Unique identifier of the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`, `not`, `in`\) and `$orderby`. |
| lastModifiedBy | String | Name of the user or application that last updated the rule. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `in`, `startsWith`, `endsWith`, `contains`\). |
| lastModifiedDateTime | DateTimeOffset | Timestamp of when the rule was last updated. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `le`, `ge`, `lt`, `gt`\) and `$orderby`. |
| queryCondition | [microsoft.graph.security.queryCondition](https://learn.microsoft.com/en-us/graph/api/resources/security-querycondition?view=graph-rest-beta) | The advanced hunting query that defines the detection logic of this rule. Supports `$filter` on **queryCondition/queryText** \(String\) with `eq`, `ne`, `not`, `in`, `startsWith`, `endsWith`, `contains`. |
| schedule | [microsoft.graph.security.ruleSchedule](https://learn.microsoft.com/en-us/graph/api/resources/security-ruleschedule?view=graph-rest-beta) | The triggering schedule of this rule. Supports `$filter` on **schedule/frequency** \(Duration\) with `eq`, `ne`, `not`, `le`, `ge`, `lt`, `gt`. Supports `$orderby` on **schedule/frequency** and **schedule/nextRunDateTime**. |
| status | microsoft.graph.security.detectionRuleStatus | The current run status of the rule. The possible values are: `enabled`, `disabled`, `autoDisabled`, `unknownFutureValue`. Supports `$filter` \(`eq`, `ne`, `not`, `in`\) and `$orderby`. |
| detectorId \(deprecated\) | String | Internal detector identifier. **Deprecated.** This property will be removed from this resource on 2026-10-01. |
| isEnabled \(deprecated\) | Boolean | Indicates whether the rule is turned on for the tenant. Supports `$filter` \(`eq`, `ne`, `not`\). **Deprecated.** Use **status** instead. This property will be removed from this resource on 2026-10-01. |
| detectionAction | [microsoft.graph.security.detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-beta) | The actions taken when a detection is made by this rule, including the alert that is created and any automated response actions. Supports `$filter` on the following nested **alertTemplate** properties:  <br><br><br><li>String: <strong>detectionAction/alertTemplate/title</strong>, <strong>detectionAction/alertTemplate/description</strong>, <strong>detectionAction/alertTemplate/category</strong>, <strong>detectionAction/alertTemplate/recommendedActions</strong> — each supports <code>eq</code>, <code>ne</code>, <code>not</code>, <code>in</code>, <code>startsWith</code>, <code>endsWith</code>, <code>contains</code>.</li><br><br><li>Enum: <strong>detectionAction/alertTemplate/severity</strong> — supports <code>eq</code>, <code>ne</code>, <code>not</code>, <code>in</code>.</li> |
| lastRunDetails \(deprecated\) | [microsoft.graph.security.runDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-rundetails?view=graph-rest-beta) | Runtime execution details for the most recent rule run. Supports `$filter` on the following nested properties:  <br><br><br><li>String: <strong>lastRunDetails/failureReason</strong> — supports <code>eq</code>, <code>ne</code>, <code>not</code>, <code>in</code>, <code>startsWith</code>, <code>endsWith</code>, <code>contains</code>.</li><br><br><li>DateTimeOffset: <strong>lastRunDetails/lastRunDateTime</strong> — supports <code>eq</code>, <code>ne</code>, <code>not</code>, <code>le</code>, <code>ge</code>, <code>lt</code>, <code>gt</code>.</li><br><br><li>Enum: <strong>lastRunDetails/status</strong>, <strong>lastRunDetails/errorCode</strong> — each supports <code>eq</code>, <code>ne</code>, <code>not</code>, <code>in</code>.</li><br><br>**Deprecated.** This property will be removed from this resource on 2026-10-01. Runtime execution details aren't exposed in the v1.0 API. |

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
  },
  "detectorId": "String",
  "isEnabled": "Boolean",
  "lastRunDetails": {
    "@odata.type": "microsoft.graph.security.runDetails"
  }
}
```
