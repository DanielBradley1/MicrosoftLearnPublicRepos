<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-07 -->

# driveProtectionRule resource type

Namespace: microsoft.graph

Represents a protection rule associated with a [OneDrive for Business protection policy](https://learn.microsoft.com/en-us/graph/api/resources/onedriveforbusinessprotectionpolicy?view=graph-rest-1.0).

Inherits from [protectionRuleBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/onedriveforbusinessprotectionpolicy-list-driveinclusionrules?view=graph-rest-1.0) | [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0) collection | Get a list of the [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/protectionrulebase-post?view=graph-rest-1.0) | [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0) | Create a new [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/protectionrulebase-get?view=graph-rest-1.0) | [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0) | Read the properties and relationships of a [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0). |
| [Update](https://learn.microsoft.com/en-us/graph/api/protectionrulebase-update?view=graph-rest-1.0) | [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0) | Update the properties of a [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/protectionrulebase-delete?view=graph-rest-1.0) | None | Delete a [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0). |
| [Delete and unprotect](https://learn.microsoft.com/en-us/graph/api/protectionrulebase-deleteandunprotect?view=graph-rest-1.0) | [driveProtectionRule](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0) | Delete and unprotect all the artifacts protected by a dynamic rule. |
| [Run](https://learn.microsoft.com/en-us/graph/api/protectionrulebase-run?view=graph-rest-1.0) | [protectionRuleBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0) | Activate a drive protection rule. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the protection rule associated with the policy. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) entitySet | The identity of the person who created the rule. |
| createdDateTime | DateTimeOffset | The date and time that the rule was created. |
| driveExpression | String | Contains a drive expression. For examples, see [driveExpression examples](https://learn.microsoft.com/en-us/graph/api/resources/driveprotectionrule?view=graph-rest-1.0#driveexpression-examples). |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | If the operation fails, contain the details of the error. |
| isAutoApplyEnabled | Boolean | `true` indicates that the protection rule is dynamic; `false` that it's static. Static rules run one time while dynamic rules listen to all changes in the system and update the protection unit list. Currently, only static rules are supported. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the person who last modified this rule. |
| lastModifiedDateTime | DateTimeOffset | The timestamp of the last modification to this rule. |
| status | [protectionRuleStatus](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0#protectionrulestatus-values) | The status of the protection rule. The possible values are: `draft`, `active`, `completed`, `completedWithErrors`, `unknownFutureValue`, `updateRequested`, `deleteRequested`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `updateRequested` , `deleteRequested`. The `draft` member is currently unsupported. Inherited from [protectionRuleBase](https://learn.microsoft.com/en-us/graph/api/resources/protectionrulebase?view=graph-rest-1.0). |

### driveExpression examples

The following table shows possible formats for the drive expression.

| Property | Operator | Example |
| --- | --- | --- |
| `memberOf` | `-any` | `(memberOf -any (group.id -in ['d7f5150a-0c6f-4894-a6a1-6df77b26f375']))` |
| `group.id` | `-in` | `(memberOf -any (group.id -in ['d7f5150a-0c6f-4894-a6a1-6df77b26f375', '363cdbd0-f091-4644-93e4-64c1020c94d8']))` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driveProtectionRule",
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
  "driveExpression": "String"
}
```
