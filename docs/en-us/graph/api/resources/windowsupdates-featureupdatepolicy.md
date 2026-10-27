<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-featureupdatepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# featureUpdatePolicy resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an entity that governs the feature update deployment settings content for an associated deployment audience. This audience can consist of one or more Microsoft Entra groups.

Inherits from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [policy resource](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) base type. Operations are performed through the base type endpoints.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalRules | [microsoft.graph.windowsUpdates.approvalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-approvalrule?view=graph-rest-beta) collection | The rules that determine how matching feature update content is approved. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the feature update policy is created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| description | String | The feature update policy description. The maximum length is 1,500 characters. Inherited from [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| displayName | String | The feature update policy display name. The maximum length is 200 characters. Inherited from [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| id | String | The policy unique identifier. Inherited from [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the feature update policy was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| applicableCatalogs | [microsoft.graph.windowsUpdates.applicableCatalog](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalog?view=graph-rest-beta) collection | The feature update catalog entries that apply to devices targeted by the policy. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| applicableContent | [microsoft.graph.windowsUpdates.applicableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontent?view=graph-rest-beta) collection | The existing applicable-content collection. For feature update applicability, use **applicableCatalogs**. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| approvals | [microsoft.graph.windowsUpdates.policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) collection | Represents a set of feature updates policy approval types. Inherited from [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| rings | [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) collection | Represents a set of deployment rings that contains update deployment settings. Inherited from [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.featureUpdatePolicy",
  "approvalRules": [{"@odata.type": "microsoft.graph.windowsUpdates.approvalRule"}],
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
