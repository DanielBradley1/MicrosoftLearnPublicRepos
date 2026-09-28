<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationidentitysyncpolicytemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# multiTenantOrganizationIdentitySyncPolicyTemplate resource type

Namespace: microsoft.graph

Defines an optional cross-tenant access policy template with user synchronization settings for multitenant organization tenants. Each tenant has its own template. For more information, see [crossTenantIdentitySyncPolicyPartner resource type](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantidentitysyncpolicypartner?view=graph-rest-1.0).

- If your tenant is joining a multitenant organization, the template is applicable to the user synchronization settings for all multitenant organization tenants.
- If another tenant joins your multitenant organization, the template is applicable only to the user synchronization settings of the newly joined multitenant organization tenant.

Whether the template is applied to the user synchronization settings of relevant tenants is configurable with the `templateApplicationLevel` property.

- If the template is configured to apply, it is only applied to user synchronization properties where the corresponding template property has a non-null value.

In its default and unconfigured state, where all template properties \(other than `templateApplicationLevel`\) are null, the template has no effect on user synchronization settings.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationidentitysyncpolicytemplate-get?view=graph-rest-1.0) | [multiTenantOrganizationIdentitySyncPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationidentitysyncpolicytemplate?view=graph-rest-1.0) | Get the user synchronization settings of the template. |
| [Update](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationidentitysyncpolicytemplate-update?view=graph-rest-1.0) | [multiTenantOrganizationIdentitySyncPolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganizationidentitysyncpolicytemplate?view=graph-rest-1.0) | Update the user synchronization settings of the template. |
| [Reset](https://learn.microsoft.com/en-us/graph/api/multitenantorganizationidentitysyncpolicytemplate-resettodefaultsettings?view=graph-rest-1.0) | None | Reset the user synchronization settings of the template to the default values. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of the template. Key. |
| templateApplicationLevel | templateApplicationLevel | Specifies whether the template will be applied to user synchronization settings of certain tenants. The possible values are: `none`, `newPartners`, `existingPartners`, `unknownFutureValue`. You can also specify multiple values like `newPartners,existingPartners` \(default\). `none` indicates the template isn't applied to any new or existing partner tenants. `newPartners` indicates the template is applied to new partner tenants. `existingPartners` indicates the template is applied to existing partner tenants, those who already had partner-specific user synchronization settings in place. |
| userSyncInbound | [crossTenantUserSyncInbound](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantusersyncinbound?view=graph-rest-1.0) | Defines whether users can be synchronized from the partner tenant. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantOrganizationIdentitySyncPolicyTemplate",
  "templateApplicationLevel": "String",
  "userSyncInbound": {
    "@odata.type": "microsoft.graph.crossTenantUserSyncInbound"
  }
}
```
