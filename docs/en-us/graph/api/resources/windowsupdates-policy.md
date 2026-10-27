<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# windowsUpdates policy resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that governs the update deployment settings content for an associated deployment audience. This audience can consist of one or more Microsoft Entra groups. You can't instantiate this resource directly; use one of its derived types.

Base type of [driverUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatepolicy?view=graph-rest-beta), [featureUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-featureupdatepolicy?view=graph-rest-beta), and [qualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatepolicy?view=graph-rest-beta). Instances in a policy collection are differentiated by the **@odata.type** property, which identifies the derived type of each object.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List policies](https://learn.microsoft.com/en-us/graph/api/windowsupdates-adminwindowsupdates-list-policies?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) collection | Get a list of the [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) objects and their properties. |
| [Create policy](https://learn.microsoft.com/en-us/graph/api/windowsupdates-adminwindowsupdates-post-policies?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) | Create a new Windows update [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) object. |
| [Get policy](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) | Read the properties and relationships of a [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) object. |
| [Update policy](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-update?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) | Update the properties of a [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) object. |
| [Delete policy](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-delete?view=graph-rest-beta) | None | Delete a Windows update [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) object. |
| [List applicableCatalogs](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-list-applicablecatalogs?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableCatalog](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalog?view=graph-rest-beta) collection | List catalog entries that are applicable to devices targeted by the policy. |
| [List applicableContent](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-list-applicablecontent?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.applicableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontent?view=graph-rest-beta) collection | List [applicable update content](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontent?view=graph-rest-beta) to offer to Microsoft Entra groups, Windows Autopatch groups, or both. |
| [List approvals](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-list-approvals?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) collection | Get a list of the [policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) objects and their properties. |
| [Create policyApproval](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-post-approvals?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) | Create a new [policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) object. |
| [List rings](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-list-rings?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) collection | Get a list of the [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) objects and their properties. |
| [Create ring](https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-post-rings?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) | Create a new [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalRules | [microsoft.graph.windowsUpdates.approvalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-approvalrule?view=graph-rest-beta) collection | The approved rule of the policy that determines which published content matches the rule on an ongoing basis. |
| createdDateTime | DateTimeOffset | The date and time when the policy is created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| description | String | The policy description. The maximum length is 1,500 characters. |
| displayName | String | The policy display name. The maximum length is 200 characters. |
| id | String | The policy unique identifier. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the policy was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| applicableCatalogs | [microsoft.graph.windowsUpdates.applicableCatalog](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalog?view=graph-rest-beta) collection | The catalog entries that apply to devices targeted by the policy. |
| applicableContent | [microsoft.graph.windowsUpdates.applicableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontent?view=graph-rest-beta) collection | The existing applicable-content collection. For driver and feature update applicability, use **applicableCatalogs**. |
| approvals | [microsoft.graph.windowsUpdates.policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) collection | The update content approvals associated with the policy. |
| rings | [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) collection | The deployment rings that define targeting, deferral, and pause settings for the policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.policy",
  "approvalRules": [{"@odata.type": "microsoft.graph.windowsUpdates.approvalRule"}],
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
