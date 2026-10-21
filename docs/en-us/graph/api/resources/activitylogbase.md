<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-10 -->

# activityLogBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an activity log record that contains information about any admin activity on backup and restore resources.

Base type for [backupPolicyActivityLog](https://learn.microsoft.com/en-us/graph/api/resources/backuppolicyactivitylog?view=graph-rest-beta), [dynamicRuleActivityLog](https://learn.microsoft.com/en-us/graph/api/resources/dynamicruleactivitylog?view=graph-rest-beta), [offboardingActivityLog](https://learn.microsoft.com/en-us/graph/api/resources/offboardingactivitylog?view=graph-rest-beta), and [restoreTaskActivityLog](https://learn.microsoft.com/en-us/graph/api/resources/restoretaskactivitylog?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-activitylogs?view=graph-rest-beta) | [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta) collection | Get a list of [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityType | [activityLogOperationType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#activitylogoperationtype-values) | The type of activity performed. The possible values are: `backupPolicyCreated`, `backupPolicyActivated`, `backupPolicyModified`, `backupPolicyPaused`, `backupPolicyRenamed`, `dynamicRuleExecution`, `dynamicRuleDeletion`, `protectionUnitLevelOffboarding`, `policyLevelOffboarding`, `restoreTaskCreated`, `restoreTaskCompleted`, `backupPolicyDeleted`, `unknownFutureValue`. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | Contains error details if an error occurred while processing this activity. |
| eventDateTime | DateTimeOffset | Timestamp of activity completion. |
| id | String | The unique identifier of the activityLog. |
| performedBy | String | The identity of the person who performed the activity. |
| resultStatus | [activityLogResultStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#activitylogresultstatus-values) | Indicates the outcome status of the activity. The possible values are: `succeeded`, `failed`, `partiallySucceeded`, `unknownFutureValue`. |
| serviceType | [serviceType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#servicetype-values) | Represents the service type. The possible values are: `unknown`, `sharepoint`, `exchange`, `oneDriveForBusiness`, `unknownFutureValue`. |
| severity | [activityLogSeverity](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#activitylogseverity-values) | Indicates the severity of the activity. The possible values are: `high`, `medium`, `low`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.activityLogBase",
  "id": "String (identifier)",
  "eventDateTime": "String (timestamp)",
  "activityType": "String",
  "resultStatus": "String",
  "serviceType": "String",
  "severity": "String",
  "performedBy": "String",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  }
}
```
