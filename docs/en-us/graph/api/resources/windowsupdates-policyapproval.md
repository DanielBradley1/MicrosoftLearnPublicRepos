<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# policyApproval resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an approval of Windows update content for a policy.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List approvals](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-list-approvals?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) collection | Get a list of the [policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) objects and their properties. |
| [Create policyApproval](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-post-approvals?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) | Create a new [policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) object. |
| [Get policyApproval](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policyapproval-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) | Read the properties and relationships of a [policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) object. |
| [Update policyApproval](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policyapproval-update?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) | Update the properties of a [policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) object. |
| [Delete policyApproval](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policyapproval-delete?view=graph-rest-beta) | None | Delete a [policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvedBy | [windowsUpdates.approvedBy](https://learn.microsoft.com/en-us/graph/api/resources/enums-windowsupdates?view=graph-rest-beta#approvedby-values) | Identifies who approved the content. The possible values are: `system`, `user`, `unknownFutureValue`. This property is set by the service. Read-only. |
| catalogEntryId | String | The catalog entry ID to approve. |
| createdDateTime | DateTimeOffset | The date and time the policy approval is created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | The unique identifier for the policy approval. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time the policy approval was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| startDateTime | DateTimeOffset | The date and time when the approved content can start being offered. If omitted when the approval is created, the service uses the current time. |
| status | [windowsUpdates.approvalStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-windowsupdates?view=graph-rest-beta#approvalstatus-values) | The approval status. The possible values are: `approved`, `suspended`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| catalogEntry | [microsoft.graph.windowsUpdates.catalogEntry](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogentry?view=graph-rest-beta) | The content that you can approve for deployment. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.policyApproval",
  "approvedBy": "String",
  "catalogEntryId": "String",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "startDateTime": "String (timestamp)",
  "status": "String"
}
```
