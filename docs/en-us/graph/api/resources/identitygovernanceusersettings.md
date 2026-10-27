<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernanceusersettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# identityGovernanceUserSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the identity governance settings of a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta).

This resource is configured in the **identityGovernance** property of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta) resource. To retrieve these settings, include `$select=identityGovernance` when you [get a user](https://learn.microsoft.com/en-us/graph/api/user-get?view=graph-rest-beta).

## Methods

None. To manage the approver delegate of a user, use the [Get approverDelegate](https://learn.microsoft.com/en-us/graph/api/approverdelegate-get?view=graph-rest-beta) and [Update approverDelegate](https://learn.microsoft.com/en-us/graph/api/approverdelegate-update?view=graph-rest-beta) methods.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| approverDelegate | [approverDelegate](https://learn.microsoft.com/en-us/graph/api/resources/approverdelegate?view=graph-rest-beta) | The user or group that approves Microsoft Entra entitlement management access package assignment requests and access reviews on behalf of the user, and the period during which the delegation is in effect. Nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernanceUserSettings",
  "approverDelegate": {
    "@odata.type": "microsoft.graph.approverDelegate"
  }
}
```
