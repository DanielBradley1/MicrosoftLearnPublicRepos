<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-07 -->

# siteProtectionRule resource type

Namespace: microsoft.graph

Represents the properties of a protection rule associated with a [sharePointProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/sharepointprotectionpolicy?view=graph-rest-1.0).

Inherits from [protectionRuleBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/sharepointprotectionpolicy-list-siteinclusionrules?view=graph-rest-1.0) | [siteProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0) collection | Get a list of [siteProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/protectionrulebase-post?view=graph-rest-1.0) | [siteProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0) | Create a new [siteProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/protectionrulebase-get?view=graph-rest-1.0) | [siteProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0) | Read the properties and relationships of a [siteProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/protectionrulebase-delete?view=graph-rest-1.0) | None | Delete a [siteProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0). |
| [Run](https://learn.microsoft.com/en-us/graph/api/protectionrulebase-run?view=graph-rest-1.0) | [protectionRuleBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0) | Activate a site protection rule. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the protection rule associated with the policy. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the person who created the rule. |
| createdDateTime | DateTimeOffset | The date and time that the rule was created. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Contains error details if any operation on a rule expression fails. |
| isAutoApplyEnabled | Boolean | `true` indicates that the protection rule is dynamic; `false` that it's static. Static rules run one time while dynamic rules listen to all changes in the system and update the protection unit list. Currently, only static rules are supported. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified the rule. |
| lastModifiedDateTime | DateTimeOffset | Timestamp of the last modification to the rule. |
| siteExpression | String | Contains a site expression. For examples, see [siteExpression example](https://learn.microsoft.com/en-us/graph/api/resources/siteprotectionrule?view=graph-rest-1.0#siteexpression-examples). |
| status | [protectionRuleStatus](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0#protectionrulestatus-values) | The status of the protection rule. Supports a subset of the values for **protectionRuleStatus**. The possible values are: `draft`, `active`, `completed`, `completedWithErrors`, `unknownFutureValue`. The `draft` member is currently unsupported. Inherited from [protectionRuleBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0). |

### siteExpression examples

The following table shows the possible formats for the site expression.

| Property | Operator | Example |
| --- | --- | --- |
| `displayName` | `-contains` | `((displayName -contains 'Finance') -or (displayName -contains 'Legal'))` |
| `lastModifiedDateTime` | `-ge` | `(((displayName -contains 'Finance') -or (webUrl -contains 'Legal')) -and (lastModifiedDateTime -ge '2024-02-26T11:36:20Z'))` |
| `webUrl` | `-contains` | `((displayName -contains 'Finance') -or (webUrl -contains 'Legal'))` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.siteProtectionRule",
  "id": "String (identifier)",
  "status": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "isAutoApplyEnabled": "Boolean",
  "siteExpression": "String"
}
```
