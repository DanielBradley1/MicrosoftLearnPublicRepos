<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskpropertyrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-16 -->

# plannerTaskPropertyRule resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents specific restrictions that apply to editing a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). For more information, see [Configuring task rules in Planner](https://learn.microsoft.com/en-us/graph/planner-task-rules-overview).

Inherits from [plannerPropertyRule](https://learn.microsoft.com/en-us/graph/api/resources/plannerpropertyrule?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appliedCategories | [plannerFieldRules](https://learn.microsoft.com/en-us/graph/api/resources/plannerfieldrules?view=graph-rest-beta) | Rules and restrictions for applied categories. This value doesn't currently support overrides. Accepted values for the default rule and individual overrides are `allow`, `block`. |
| approvalAttachment | [plannerFieldRules](https://learn.microsoft.com/en-us/graph/api/resources/plannerfieldrules?view=graph-rest-beta) | Rules and restrictions for approval. Allowed overrides are `userCreated` and `applicationCreated`. Accepted values for the default rule and individual overrides are: `allow`, `add`, `remove`, `block`. |
| assignments | [plannerFieldRules](https://learn.microsoft.com/en-us/graph/api/resources/plannerfieldrules?view=graph-rest-beta) | Rules and restrictions for assignments. Allowed overrides are `userCreated` and `applicationCreated`. Accepted values for the default rule and individual overrides are `allow`, `add`, `addSelf`, `addOther`, `remove`, `removeSelf`, `removeOther`, `block`. |
| checkLists | [plannerFieldRules](https://learn.microsoft.com/en-us/graph/api/resources/plannerfieldrules?view=graph-rest-beta) | Rules and restrictions for checklist. Allowed overrides are `userCreated` and `applicationCreated`. Accepted values for the default rule and individual overrides are `allow`, `add`, `remove`, `update`, `check`, `reorder`, `block`. |
| completionRequirements | String collection | Rules and restrictions for completion requirements of the task. Accepted values are `allow`, `add`, `remove`, `edit`, and `block`. |
| delete | String collection | Rules and restrictions for deleting the task. Accepted values are `allow` and `block`. |
| dueDate | String collection | Rules and restrictions for changing the due date of the task. Accepted values are `allow` and `block`. |
| forms | [plannerFieldRules](https://learn.microsoft.com/en-us/graph/api/resources/plannerfieldrules?view=graph-rest-beta) | Rules and restrictions for forms. Allowed overrides are `userCreated` and `applicationCreated`. The following are the accepted values for the default rule and individual overrides: `allow`, `add`, `addResponse`, `remove`, `update`, `block`. |
| move | String collection | Rules and restrictions for moving the task between buckets or plans. Accepted values are `allow`, `moveBetweenPlans`, `moveBetweenBuckets`, and `block`. |
| notes | String collection | Rules and restrictions for changing the notes of the task. Accepted values are `allow` and `block`. |
| order | String collection | Rules and restrictions for changing the order of the task. Accepted values are `allow` and `block`. |
| percentComplete | String collection | Rules and restrictions for changing the completion percentage of the task. Accepted values are `allow`, `setToComplete`, `overrideRequirements`, `setToNotStarted`, `setToInProgress`, and `block`. |
| previewType | String collection | Rules and restrictions for changing the preview type of the task. Accepted values are `allow` and `block`. |
| priority | String collection | Rules and restrictions for changing the priority of the task. Accepted values are `allow` and `block`. |
| references | [plannerFieldRules](https://learn.microsoft.com/en-us/graph/api/resources/plannerfieldrules?view=graph-rest-beta) | Rules and restrictions for references. Allowed overrides are `userCreated` and `applicationCreated`. Accepted values for the default rule and individual overrides are `allow`, `add`, `remove`, `block`. |
| ruleKind | plannerRuleKind | Identifies which type of property rules this instance represents. Must be set to `taskRule`. The possible values are: `taskRule`, `bucketRule`, `planRule`, `unknownFutureValue`. Inherited from [plannerPropertyRule](https://learn.microsoft.com/en-us/graph/api/resources/plannerpropertyrule?view=graph-rest-beta). |
| startDate | String collection | Rules and restrictions for changing the start date of the task. Accepted values are `allow` and `block`. |
| title | String collection | Rules and restrictions for changing the title of the task. Accepted values are `allow` and `block`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskPropertyRule",
  "appliedCategories": {"@odata.type": "microsoft.graph.plannerFieldRules"},
  "assignments": {"@odata.type": "microsoft.graph.plannerFieldRules"},
  "checkLists": {"@odata.type": "microsoft.graph.plannerFieldRules"},
  "approvalAttachment": {"@odata.type": "microsoft.graph.plannerFieldRules"},
  "completionRequirements": ["String"],
  "delete": ["String"],
  "dueDate": ["String"],
  "move": ["String"],
  "notes": ["String"],
  "order": ["String"],
  "percentComplete": ["String"],
  "previewType": ["String"],
  "priority": ["String"],
  "references": {"@odata.type": "microsoft.graph.plannerFieldRules"},
  "ruleKind": "String",
  "startDate": ["String"],
  "title": ["String"]
}
```
