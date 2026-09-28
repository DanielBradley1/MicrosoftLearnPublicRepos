<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# appManagementPolicy resource type

Namespace: microsoft.graph

Restrictions on app management operations for specific applications and service principals. If this resource is not configured for an application or service principal, the restrictions default to the settings in the [tenantAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/tenantappmanagementpolicy?view=graph-rest-1.0) object.

To learn more about how to use app management policy, see [Microsoft Entra application authentication methods API overview](https://learn.microsoft.com/en-us/graph/api/resources/applicationauthenticationmethodpolicy?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/appmanagementpolicy-list?view=graph-rest-1.0) | [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) | Return a list of app management policies created for applications and service principals along with their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/appmanagementpolicy-post?view=graph-rest-1.0) | [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) | Create an app management policy that can be assigned to an application or service principal object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/appmanagementpolicy-get?view=graph-rest-1.0) | [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) | Get a single app management policy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/appmanagementpolicy-update?view=graph-rest-1.0) | None | Update an app management policy. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/appmanagementpolicy-delete?view=graph-rest-1.0) | None | Delete an app management policy from the collection of policies in appManagementPolicies. |
| [List applies to](https://learn.microsoft.com/en-us/graph/api/appmanagementpolicy-list-appliesto?view=graph-rest-1.0) | [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) | Return a list of applications and service principals to which the policy is applied. |
| [Create applies to](https://learn.microsoft.com/en-us/graph/api/appmanagementpolicy-post-appliesto?view=graph-rest-1.0) | None | Assign an appManagementPolicy policy object to an application or service principal object. |
| [Delete applies to](https://learn.microsoft.com/en-us/graph/api/appmanagementpolicy-delete-appliesto?view=graph-rest-1.0) | None | Remove an appManagementPolicy policy object from an application or service principal object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| description | String | The description of the policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| id | String | The unique identifier for the policy. |
| isEnabled | Boolean | Denotes whether the policy is enabled. |
| restrictions | [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0) | Restrictions that apply to an application or service principal object. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliesTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Collection of applications and service principals to which the policy is applied. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/appManagementPolicies",
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "restrictions": {"@odata.type": "microsoft.graph.appManagementConfiguration"}
}
```
