<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# incidentTask resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a remediation action for an incident. When Microsoft Defender Experts for XDR identifies a needed action, it creates a task for you to review and act on. Review and take action on these tasks through the portal or using this API.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-list-incidenttasks?view=graph-rest-beta) | [microsoft.graph.security.incidentTask](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttask?view=graph-rest-beta) collection | Get incident task objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-incidenttask-get?view=graph-rest-beta) | [microsoft.graph.security.incidentTask](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttask?view=graph-rest-beta) | Read properties and relationships of an incident task. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-incidenttask-update?view=graph-rest-beta) | [microsoft.graph.security.incidentTask](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttask?view=graph-rest-beta) | Update the status of an incident task. |
| [Execute response action](https://learn.microsoft.com/en-us/graph/api/security-incidenttask-executeresponseaction?view=graph-rest-beta) | None | Execute a remediation action on an incident task. Limited to supported action types. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionStatus | microsoft.graph.security.incidentTaskActionStatus | The execution status of the action. The possible values are: `notStarted`, `inProgress`, `partiallyCompleted`, `completed`, `failed`, `unknownFutureValue`. For more information, see [incidentTaskActionStatus values](#incidenttaskactionstatus-values). |
| actionType | microsoft.graph.security.incidentTaskActionType | The remediation action to perform. The possible values are: `text`, `isolateDevice`, `stopAndQuarantineFile`, `runAntiVirusScan`, `collectInvestigationPackage`, `restrictAppExecution`, `submitIocRule`, `forceUserPasswordReset`, `disableUser`, `markUserAsCompromised`, `requireSignIn`, `hardDeleteEmail`, `softDeleteEmail`, `unIsolateDevice`, `unRestrictAppExecution`, `enableUser`, `unknownFutureValue`. For more information, see [incidentTaskActionType values](#incidenttaskactiontype-values). |
| createdByDisplayName | String | Name of the entity that created the task. Read-only. |
| createdDateTime | DateTimeOffset | Creation time of the task. Read-only. |
| description | String | Description of the remediation action. |
| displayName | String | Title of the task. |
| id | String | Unique GUID identifier for the task. |
| lastModifiedByDisplayName | String | Name of the entity that last updated the task. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Last update time of the task. Read-only. |
| responseAction | microsoft.graph.security.incidentTaskResponseAction | The reponse action. |
| source | microsoft.graph.security.incidentTaskSource | Origin of the task. The possible values are: `defenderExpertsGuidedResponse`, `defenderExpertsManagedResponse`, `unknownFutureValue`. For more information, see [incidentTaskSource values](#incidenttasksource-values). |
| status | microsoft.graph.security.incidentTaskStatus | Current task status. This property is the only property you can update. The possible values are: `open`, `inProgress`, `completed`, `failed`, `notRelevant`, `unknownFutureValue`. For more information, see [incidentTaskStatus values](#incidenttaskstatus-values). |

### incidentTaskActionStatus values

| Member | Description |
| :--- | :--- |
| notStarted | The action related to the incident task isn't started. |
| inProgress | The action related to the incident task is inProgress. |
| partiallyCompleted | The action related to the incident task is partially completed. |
| completed | The action related to the incident task is completed. |
| failed | The action related to the incident task is failed. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### incidentTaskActionType values

| Member | Description |
| :--- | :--- |
| text | Action could be any free text, for example, the SOC can guide the customer to format their device. |
| isolateDevice | Uses Microsoft Defender for Endpoint to apply full network isolation, preventing the device from connecting to any application or service. |
| stopAndQuarantineFile | Uses Microsoft Defender for Endpoint to delete a file from the device. |
| runAntiVirusScan | Performs Microsoft Defender Antivirus scan on the device. |
| collectInvestigationPackage | Uses Microsoft Defender for Endpoint to collect device logs and stores it in a ZIP file. |
| restrictAppExecution | Sets restrictions on device to allow only executables that are signed with a Microsoft-issued certificate to run. |
| submitIocRule | Submit IOC rule. |
| forceUserPasswordReset | Forces the user to reset their password. |
| disableUser | Temporarily prevents a user from logging in to the on-premises. |
| markUserAsCompromised | Sets the users risk level to "high" in Azure Active Directory. |
| requireSignIn | Requires the user to sign in again. |
| hardDeleteEmail | Deletes the email message. |
| softDeleteEmail | Moves the email message to the deleted folder. |
| unIsolateDevice | Reverts isolateDevice response action. |
| unRestrictAppExecution | Reverts restrictAppExecution response action. |
| enableUser | Reverts disableUser response action. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### incidentTaskSource values

| Member | Description |
| :--- | :--- |
| defenderExpertsGuidedResponse | The Defender Experts incident task is pending on the customer for execution. |
| defenderExpertsManagedResponse | The Defender Experts incident task execution is done by Defender Experts. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### incidentTaskStatus values

| Member | Description |
| :--- | :--- |
| open | The incident task is marked as open. |
| inProgress | The incident task is marked as in progress. |
| completed | The incident task is marked as completed. |
| failed | The incident task is marked as failed. Failure in action execution sets the incident task status to failed as well. |
| notRelevant | The incident task is marked as not relevant. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| incident | [microsoft.graph.security.incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-beta) | Required. The incident that contains this task. Must contain a valid incident ID. |

## JSON representation

The following JSON shows the resource type structure.

```json
{
  "@odata.type": "#microsoft.graph.security.incidentTask",
  "id": "String (identifier)",
  "status": "String",
  "source": "String",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "createdByDisplayName": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedByDisplayName": "String",
  "actionStatus": "String",
  "actionType": "String",
  "incident": {
    "@odata.type": "microsoft.graph.security.incident",
    "id": "String"
  }
}
```
