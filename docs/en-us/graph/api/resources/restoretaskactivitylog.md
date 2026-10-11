<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restoretaskactivitylog?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-10 -->

# restoreTaskActivityLog resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents activity logs related to restore task operations. This resource tracks restore task activities such as task creation and completion, including details about the restore session and artifacts.

Inherits from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-activitylogs?view=graph-rest-beta) | [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta) collection | Get a list of [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityType | [activityLogOperationType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#activitylogoperationtype-values) | The type of activity performed. The possible values are: `backupPolicyCreated`, `backupPolicyActivated`, `backupPolicyModified`, `backupPolicyPaused`, `backupPolicyRenamed`, `dynamicRuleExecution`, `dynamicRuleDeletion`, `protectionUnitLevelOffboarding`, `policyLevelOffboarding`, `restoreTaskCreated`, `restoreTaskCompleted`, `unknownFutureValue`. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| destinationType | [destinationType](https://learn.microsoft.com/en-us/graph/api/resources/restoretaskactivitylog?view=graph-rest-beta#destinationtype-values) | Specifies the type of destination where the data is being restored. The possible values are: `new`, `inPlace`, `unknownFutureValue`. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | Contains error details if an error occurred while processing this activity. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| eventDateTime | DateTimeOffset | Timestamp of activity completion. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| id | String | The unique identifier of the activityLog. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| performedBy | String | The identity of the person who performed the activity. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| restoreArtifactDetails | [restoreArtifactDetails](https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactdetails?view=graph-rest-beta) | Contains detailed information about the artifacts being restored, including counts and status of restored items. |
| restoreCompletionDateTime | DateTimeOffset | The date and time when the restore task was completed. |
| restoreSessionId | String | The unique identifier of the restore session associated with this activity log. |
| restoreSessionStatus | [restoreSessionStatus](https://learn.microsoft.com/en-us/graph/api/resources/restoretaskactivitylog?view=graph-rest-beta#restoresessionstatus-values) | Indicates the current status of the restore session. The possible values are: `draft`, `activating`, `active`, `completedWithError`, `completed`, `unknownFutureValue`, `failed`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `failed`. |
| resultStatus | [activityLogResultStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#activitylogresultstatus-values) | Indicates the outcome status of the activity. The possible values are: `succeeded`, `failed`, `partiallySucceeded`, `unknownFutureValue`. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| serviceType | [serviceType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#servicetype-values) | Represents the service type. The possible values are: `unknown`, `sharepoint`, `exchange`, `oneDriveForBusiness`, `unknownFutureValue`. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| severity | [activityLogSeverity](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#activitylogseverity-values) | Indicates the severity of the activity. The possible values are: `high`, `medium`, `low`, `unknownFutureValue`. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| tags | [restorePointTags](https://learn.microsoft.com/en-us/graph/api/resources/restoretaskactivitylog?view=graph-rest-beta#restorepointtags-values) | Indicates tags associated with the restore point used for this restore operation. The possible values are: `none`, `fastRestore`, `unknownFutureValue`. |

### destinationType values

| Member | Description |
| :--- | :--- |
| new | Data is restored to a new location. |
| inPlace | Data is restored to its original location. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### restoreSessionStatus values

| Member | Description |
| :--- | :--- |
| draft | The restore session is in draft state. |
| activating | The restore session is being activated. |
| active | The restore session is active. |
| completedWithError | The restore session completed with errors. |
| completed | The restore session completed successfully. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| failed | The restore session failed. |

### restorePointTags values

| Member | Description |
| :--- | :--- |
| none | No specific tags associated with the restore point. |
| fastRestore | The restore point supports fast restore operations. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restoreTaskActivityLog",
  "id": "String (identifier)",
  "eventDateTime": "String (timestamp)",
  "activityType": "String",
  "resultStatus": "String",
  "serviceType": "String",
  "severity": "String",
  "performedBy": "String",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "restoreSessionId": "String",
  "restoreSessionStatus": "String",
  "destinationType": "String",
  "tags": "String",
  "restoreArtifactDetails": {
    "@odata.type": "microsoft.graph.restoreArtifactDetails"
  },
  "restoreCompletionDateTime": "String (timestamp)"
}
```
