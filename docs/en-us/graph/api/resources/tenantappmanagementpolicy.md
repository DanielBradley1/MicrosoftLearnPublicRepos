<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantappmanagementpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-14 -->

# tenantAppManagementPolicy resource type

Namespace: microsoft.graph

Tenant-wide application authentication method policy to enforce app management restrictions for all applications and service principals. This policy applies to all apps and service principals unless overridden when an [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) is applied to the object.

Inherits from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/tenantappmanagementpolicy-get?view=graph-rest-1.0) | tenantAppManagementPolicy | Read the properties of the default app management policy set for applications and service principals. |
| [Update](https://learn.microsoft.com/en-us/graph/api/tenantappmanagementpolicy-update?view=graph-rest-1.0) | None | Updates the default app management policy for applications and service principals. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationRestrictions | [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0) | Restrictions that apply as default to all application objects in the tenant. |
| description | String | The description of the default policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| displayName | String | The display name of the default policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| id | String | The default policy identifier. |
| isEnabled | Boolean | Denotes whether the policy is enabled. Default value is `false`. |
| servicePrincipalRestrictions | [appManagementConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementconfiguration?view=graph-rest-1.0) | Restrictions that apply as default to all service principal objects in the tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#policies/defaultAppManagementPolicy",
  "id": "string (identifier)",
  "description": "string",
  "displayName": "string",
  "isEnabled": false,
  "applicationRestrictions": {
    "@odata.type":"microsoft.graph.appManagementConfiguration"
  },
  "servicePrincipalRestrictions": {
    "@odata.type":"microsoft.graph.appManagementConfiguration"
  }
}
```
