<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/homerealmdiscoverypolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-11 -->

# homeRealmDiscoveryPolicy resource type

Namespace: microsoft.graph

Represents a policy to control Microsoft Entra authentication behavior for federated users, in particular for autoacceleration and user authentication restrictions in federated domains. You can set **homeRealmDiscoveryPolicy** for all service principals in your organization, or for specific service principals in your organization. For more scenario and policy details, see [Configure Microsoft Entra sign-in behavior for an application by using a Home Realm Discovery policy](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/configure-authentication-for-federated-users-portal) and [Sign-in to Microsoft Entra ID using email as an alternate login ID](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-authentication-use-email-signin).

Inherits from [stsPolicy](https://learn.microsoft.com/en-us/graph/api/resources/stspolicy?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/homerealmdiscoverypolicy-list?view=graph-rest-1.0) | [homeRealmDiscoveryPolicy](https://learn.microsoft.com/en-us/graph/api/resources/homerealmdiscoverypolicy?view=graph-rest-1.0) | Read properties and relationships of homeRealmDiscoveryPolicies objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/homerealmdiscoverypolicy-post-homerealmdiscoverypolicies?view=graph-rest-1.0) | [homeRealmDiscoveryPolicy](https://learn.microsoft.com/en-us/graph/api/resources/homerealmdiscoverypolicy?view=graph-rest-1.0) | Create a homeRealmDiscoveryPolicy object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/homerealmdiscoverypolicy-get?view=graph-rest-1.0) | [homeRealmDiscoveryPolicy](https://learn.microsoft.com/en-us/graph/api/resources/homerealmdiscoverypolicy?view=graph-rest-1.0) | Read properties and relationships of a homeRealmDiscoveryPolicy object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/homerealmdiscoverypolicy-update?view=graph-rest-1.0) | None | Update a homeRealmDiscoveryPolicy object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/homerealmdiscoverypolicy-delete?view=graph-rest-1.0) | None | Delete a homeRealmDiscoveryPolicy object. |
| [List applies to](https://learn.microsoft.com/en-us/graph/api/homerealmdiscoverypolicy-list-appliesto?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the list of directoryObjects that this policy has been applied to. |
| [Assign to service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-homerealmdiscoverypolicies?view=graph-rest-1.0) | None | Assign a homeRealmDiscoveryPolicy object to a [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) object. |
| [List assigned to service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-homerealmdiscoverypolicies?view=graph-rest-1.0) | [homeRealmDiscoveryPolicy](https://learn.microsoft.com/en-us/graph/api/resources/homerealmdiscoverypolicy?view=graph-rest-1.0) collection | List the homeRealmDiscoveryPolicy objects that are assigned to a [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) object. |
| [Unassign from service principal](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-homerealmdiscoverypolicies?view=graph-rest-1.0) | None | Remove a homeRealmDiscoveryPolicy object from a [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| definition | String collection | A string collection containing a JSON string that defines the rules and settings for this policy. For more information about the JSON schema for this property, see [Properties of a home realm discovery policy definition](#properties-of-a-home-realm-discovery-policy-definition). Required. |
| description | String | Description for this policy. |
| displayName | String | Display name for this policy. Required. |
| id | String | Unique identifier for this policy. Read-only. |
| isOrganizationDefault | Boolean | If set to `true`, activates this policy. There can be many policies for the same policy type, but only one can be activated as the organization default. Optional, default value is `false`. |

### Properties of a home realm discovery policy definition

The following object shows the properties that form the JSON object for a token lifetime policy definition. This JSON object must be **converted to a string with quotations escaped** to be inserted into the **definition** property as shown in the following example.

```json
"definition": [
    "{
        \"HomeRealmDiscoveryPolicy\": {
          \"AccelerateToFederatedDomain\":true,
          \"AllowCloudPasswordValidation\": false,
          \"PreferredDomain\":\"federated.example.edu\",
          \"AlternateIdLogin\":{
            \"Enabled\":true
          }
        }
      }"
  ]
```

| Property | Type | Description |
| :--- | :--- | :--- |
| AccelerateToFederatedDomain | Boolean | Set to `true` for autoacceleration \(bypass home realm discovery\). If `true` and there's only one verified and federated domain in the tenant, then users are taken straight to the federated identity provider \(such as ADFS\) for sign in. If `true` and there's more than one verified domain in the tenant, **PreferredDomain** must be specified. Optional. |
| AllowCloudPasswordValidation | Boolean | Set to `true` to allow an application to authenticate a federated user by presenting username/password credentials directly to the Microsoft Entra token endpoint. Only works if Password Hash Sync is enabled. Optional. |
| AlternateIdLogin | Json | Set to `{\"Enabled\": true}` to allow Microsoft Entra sign-in using email as [an alternate login ID](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-authentication-use-email-signin). Only works when **IsOrganizationDefault** is set to `true`. Optional. |
| PreferredDomain | String | Specifies a domain to accelerate sign-in to. It can be omitted if the tenant has only one federated domain. If it's omitted, and there's more than one verified federated domain, this policy has no effect. Required if **AccelerateToFederatedDomain** is `true`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appliesTo | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection that this policy has been applied to. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "definition": ["String"],
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isOrganizationDefault": true
}
```
