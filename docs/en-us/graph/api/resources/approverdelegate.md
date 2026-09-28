<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approverdelegate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# approverDelegate resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an approver delegate configuration that consists of a delegate \(subject set\) and a schedule. When set, the delegate can approve or deny Entitlement Management access package requests and Access Review decisions on behalf of the primary approver. The delegation applies across all Entitlement Management access package requests and Access Reviews assigned to the user. Only [singleUser](https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-beta) and [groupMembers](https://learn.microsoft.com/en-us/graph/api/resources/groupmembers?view=graph-rest-beta) implementations of [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-beta) are currently supported as delegate targets.

## Methods

None. Use the operations on the parent resource [identityGovernanceUserSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernanceusersettings?view=graph-rest-beta) to manage the approver delegate.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| delegate | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-beta) | The identity that receives the approval delegation. Only [singleUser](https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-beta) and [groupMembers](https://learn.microsoft.com/en-us/graph/api/resources/groupmembers?view=graph-rest-beta) are currently supported. |
| schedule | [requestSchedule](https://learn.microsoft.com/en-us/graph/api/resources/requestschedule?view=graph-rest-beta) | The schedule for the delegation, including start date and expiration pattern \(duration, end date, or no expiration\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approverDelegate",
  "schedule": {
    "@odata.type": "microsoft.graph.requestSchedule"
  },
  "delegate": {
    "@odata.type": "microsoft.graph.subjectSet"
  }
}
```
