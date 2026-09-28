<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# entitlementManagementSettings resource type

Namespace: microsoft.graph

Represents settings that control the behavior of [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0). This resource doesn't include the catalog creators setting; to view or change the catalog creators role membership, use the [role assignments](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) API with the entitlement management RBAC provider.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/entitlementmanagementsettings-get?view=graph-rest-1.0) | [entitlementManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementsettings?view=graph-rest-1.0) | Read the properties of an **entitlementManagementSettings** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/entitlementmanagementsettings-update?view=graph-rest-1.0) | [entitlementManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementsettings?view=graph-rest-1.0) | Update the properties of an **entitlementManagementSettings** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| durationUntilExternalUserDeletedAfterBlocked | Duration | If **externalUserLifecycleAction** is `blockSignInAndDelete`, the duration, typically many days, after an external user is blocked from sign in before their account is deleted. |
| externalUserLifecycleAction | accessPackageExternalUserLifecycleAction | Automatic action that the service should take when an external user's last access package assignment is removed. The possible values are: `none`, `blockSignIn`, `blockSignInAndDelete`, `unknownFutureValue`. |
| id | String | A constant. Read-only. |

## Relationships

None.

## JSON representation

Here's is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.entitlementManagementSettings",
  "durationUntilExternalUserDeletedAfterBlocked": "String (duration)",
  "externalUserLifecycleAction": "String",
  "id": "String"
}
```
