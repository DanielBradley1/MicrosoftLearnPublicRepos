<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# crossTenantAccessPolicy resource type

Namespace: microsoft.graph

Represents the base policy in the directory for cross-tenant access settings.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicy-get?view=graph-rest-1.0) | [crossTenantAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy?view=graph-rest-1.0) | Read the properties and relationships of a [crossTenantAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/crosstenantaccesspolicy-update?view=graph-rest-1.0) | [crossTenantAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy?view=graph-rest-1.0) | Update the properties of a [crossTenantAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the cross-tenant access policy. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-1.0). |
| allowedCloudEndpoints | String collection | Used to specify which Microsoft clouds an organization would like to collaborate with. By default, this value is empty. Supported values for this field are: `microsoftonline.com`, `microsoftonline.us`, and `partner.microsoftonline.cn`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| default | [crossTenantAccessPolicyConfigurationDefault](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationdefault?view=graph-rest-1.0) | Defines the default configuration for how your organization interacts with external Microsoft Entra organizations. |
| partners | [crossTenantAccessPolicyConfigurationPartner](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicyconfigurationpartner?view=graph-rest-1.0) collection | Defines partner-specific configurations for external Microsoft Entra organizations. |
| templates | [policyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/policytemplate?view=graph-rest-1.0) | Represents the base policy in the directory for multitenant organization settings. |

## JSON representation

The following JSON representation shows the resource type. The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantAccessPolicy",
  "displayName": "String",
  "allowedCloudEndpoints": ["String"]
}
```
