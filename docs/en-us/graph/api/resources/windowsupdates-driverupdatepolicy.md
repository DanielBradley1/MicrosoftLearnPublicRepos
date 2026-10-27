<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# driverUpdatePolicy resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a policy that manages driver and firmware update approvals and deployments for targeted devices. Use the policy's approval rules and deployment rings to control when matching updates are approved and how they're offered.

Inherits from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [policy resource](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) base type. Operations are performed through the base type endpoints.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approvalRules | [microsoft.graph.windowsUpdates.approvalRule](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-approvalrule?view=graph-rest-beta) collection | The rules that determine how matching driver and firmware update content is approved. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the policy was created. Read-only. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| description | String | The policy description. The maximum length is 1,500 characters. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| displayName | String | The policy display name. The maximum length is 200 characters. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| id | String | The unique identifier for the policy. Read-only. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the policy was last modified. Read-only. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| applicableCatalogs | [microsoft.graph.windowsUpdates.applicableCatalog](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecatalog?view=graph-rest-beta) collection | The driver and firmware update catalog entries that apply to devices targeted by the policy. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| applicableContent | [microsoft.graph.windowsUpdates.applicableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontent?view=graph-rest-beta) collection | The existing applicable-content collection. For driver and firmware update applicability, use **applicableCatalogs**. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| approvals | [microsoft.graph.windowsUpdates.policyApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policyapproval?view=graph-rest-beta) collection | The update content approvals associated with the policy. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |
| rings | [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) collection | The deployment rings that define targeting, deferral, and pause settings for the policy. Inherited from [policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdatePolicy",
  "approvalRules": [
    {
      "@odata.type": "microsoft.graph.windowsUpdates.driverUpdateApprovalRule"
    }
  ],
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
