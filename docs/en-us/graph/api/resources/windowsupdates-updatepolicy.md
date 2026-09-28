<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# updatePolicy resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an entity that governs the deployment of content to an associated [deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List updatePolicies](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-list-updatepolicies?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) objects and their properties. |
| [Create updatePolicy](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-post-updatepolicies?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) | Create a new [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) object. |
| [Get updatePolicy](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatepolicy-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) | Read the properties and relationships of an [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) object. |
| [Update updatePolicy](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatepolicy-update?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) | Update the properties of an [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) object. |
| [Delete updatePolicy](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatepolicy-delete?view=graph-rest-beta) | None | Delete an [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) object. |
| [List complianceChanges](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatepolicy-list-compliancechanges?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta) collection | Get the complianceChange resources from the complianceChanges navigation property. |
| [Create contentApproval](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatepolicy-post-compliancechanges-contentapproval?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) | Create a new complianceChange object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| complianceChangeRules | [microsoft.graph.windowsUpdates.complianceChangeRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechangerule?view=graph-rest-beta) collection | Rules for governing the automatic creation of compliance changes. |
| createdDateTime | DateTimeOffset | The date and time when the update policy was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| deploymentSettings | [microsoft.graph.windowsUpdates.deploymentSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentsettings?view=graph-rest-beta) | Settings for governing how to deploy **content**. |
| id | String | Unique identifier for the update policy. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| audience | [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) | Specifies the audience to target. |
| complianceChanges | [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta) collection | Compliance changes like content approvals which result in the automatic creation of deployments using the **audience** and **deploymentSettings** of the policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.updatePolicy",
  "complianceChangeRules": [{"@odata.type": "microsoft.graph.windowsUpdates.contentApprovalRule"}],
  "createdDateTime": "String (timestamp)",
  "deploymentSettings": {"@odata.type": "microsoft.graph.windowsUpdates.deploymentSettings"},
  "id": "String (identifier)"
}
```
