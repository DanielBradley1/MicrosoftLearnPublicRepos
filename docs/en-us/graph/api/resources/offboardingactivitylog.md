<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/offboardingactivitylog?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-10 -->

# offboardingActivityLog resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents activity logs related to offboarding operations. This resource tracks offboarding activities at both the protection unit level and policy level.

Inherits from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/backuprestoreroot-list-activitylogs?view=graph-rest-beta) | [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta) collection | Get a list of [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityType | [activityLogOperationType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#activitylogoperationtype-values) | The type of activity performed. The possible values are: `backupPolicyCreated`, `backupPolicyActivated`, `backupPolicyModified`, `backupPolicyPaused`, `backupPolicyRenamed`, `dynamicRuleExecution`, `dynamicRuleDeletion`, `protectionUnitLevelOffboarding`, `policyLevelOffboarding`, `restoreTaskCreated`, `restoreTaskCompleted`, `backupPolicyDeleted`, `unknownFutureValue`. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | Contains error details if an error occurred while processing this activity. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| eventDateTime | DateTimeOffset | Timestamp of activity completion. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| id | String | The unique identifier of the activityLog. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| offboardingDetails | [offboardingDetails](https://learn.microsoft.com/en-us/graph/api/resources/offboardingdetails?view=graph-rest-beta) | Contains detailed information about the offboarding operation, including affected protection units and their status. |
| performedBy | String | The identity of the person who performed the activity. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| policyId | String | The unique identifier of the protection policy associated with the activity log. |
| policyName | String | Name of the protection policy. |
| policyStatus | [protectionPolicyStatus](https://learn.microsoft.com/en-us/graph/api/resources/protectionpolicybase?view=graph-rest-beta#protectionpolicystatus-values) | The aggregated status of the protection units associated with the policy. The possible values are: `inactive`, `activeWithErrors`, `updating`, `active`, `unknownFutureValue`, `dormant`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `dormant`. |
| resultStatus | [activityLogResultStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#activitylogresultstatus-values) | Indicates the outcome status of the activity. The possible values are: `succeeded`, `failed`, `partiallySucceeded`, `unknownFutureValue`. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| serviceType | [serviceType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#servicetype-values) | Represents the service type. The possible values are: `unknown`, `sharepoint`, `exchange`, `oneDriveForBusiness`, `unknownFutureValue`. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |
| severity | [activityLogSeverity](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#activitylogseverity-values) | Indicates the severity of the activity. The possible values are: `high`, `medium`, `low`, `unknownFutureValue`. Inherited from [activityLogBase](https://learn.microsoft.com/en-us/graph/api/resources/activitylogbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.offboardingActivityLog",
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
  "policyId": "String",
  "policyName": "String",
  "policyStatus": "String",
  "offboardingDetails": {
    "@odata.type": "microsoft.graph.offboardingDetails"
  }
}
```
