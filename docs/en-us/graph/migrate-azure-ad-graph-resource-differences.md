<!-- Source: https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-resource-differences -->
<!-- Sitemap-Last-Modified: 2025-02-21 -->

# Differences between resources in Azure AD Graph and Microsoft Graph

> This article is part of *Step 1: review API differences* in the [Azure AD Graph app migration planning checklist](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist) series.

When migrating apps from Azure Active Directory \(Azure AD\) Graph to Microsoft Graph, some resources have different names and different types. For example, if your Azure AD Graph app uses the **TenantDetail** resource, you need to update your code to refer to [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization) instead.

This article highlights differences between Azure AD Graph and Microsoft Graph resources. It shows resources that have different names or aren't available; it also highlights resources available in the `beta` version of Microsoft Graph but not in the `v1.0` version.

If a resource is **not** shown in this list, it's already available in the [v1.0 version](https://learn.microsoft.com/en-us/graph/api/overview) of Microsoft Graph, with the same name as in Azure AD Graph.

Note

Resource type names in Azure AD Graph are Pascal-cased, whereas in Microsoft Graph they're camel-cased.

| Azure AD Graph  <br>\(v1.6\) resource | Microsoft Graph  <br>resource | Comments |
| --- | --- | --- |
| [CertificateAuthorityInformation](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - [certificateAuthority](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthority?view=graph-rest-beta&preserve-view=true)  <br>v1.0 - [certificateAuthority](https://learn.microsoft.com/en-us/graph/api/resources/certificateauthority) |  |
| [Contact](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgContact?view=graph-rest-beta&preserve-view=true)  <br>v1.0 - [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgContact) |  |
| [DirectoryLinkChange](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - *New approach*  <br>v1.0 - *New approach* | Delta query supports relationship change detection with a mechanism that doesn't require this resource. See [Feature differences between Azure AD Graph and Microsoft Graph](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-feature-differences#differential-queries). |
| [OAuth2Permission](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - [permissionScope](https://learn.microsoft.com/en-us/graph/api/resources/permissionScope?view=graph-rest-beta&preserve-view=true)  <br>v1.0 - [permissionScope](https://learn.microsoft.com/en-us/graph/api/resources/permissionScope) |  |
| [Policy](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - [policyRoot](https://learn.microsoft.com/en-us/graph/api/resources/policyroot?view=graph-rest-beta&preserve-view=true)  <br>v1.0 - [policyRoot](https://learn.microsoft.com/en-us/graph/api/resources/policyroot) | Each type of policy has a unique type name and structure, under the **policies** URL path segment, in Microsoft Graph. In Azure AD Graph, the type was a single policy type. For example, for Azure AD Graph you would work with the **Policy** resource, and set the **type** property to `TokenIssuancePolicy`, while in Microsoft Graph the resource would be the **tokenIssuancePolicy** resource. |
| [ProvisioningError](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - *Not available*  <br>v1.0 - *Not available* | This resource is deprecated. However, a new resource describing any AD Connect related provisioning errors can be found in [onPremisesProvisioningError](https://learn.microsoft.com/en-us/graph/api/resources/onPremisesProvisioningError). |
| [ServiceEndpoint](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - [endpoint](https://learn.microsoft.com/en-us/graph/api/resources/endpoint?view=graph-rest-beta&preserve-view=true)  <br>v1.0 - [endpoint](https://learn.microsoft.com/en-us/graph/api/resources/endpoint) | **endpoints** are only available as part of the [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta&preserve-view=true) and [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal)resources in beta, and the [group](https://learn.microsoft.com/en-us/graph/api/resources/group) resource in both beta and v1.0. |
| [SignInName](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - *New approach*  <br>v1.0 - *New approach* | New modeling for the identifiers used to sign into a user account. For more information, see [objectIdentity](https://learn.microsoft.com/en-us/graph/api/resources/objectIdentity) resource type. Supports Azure AD B2C scenarios. |
| [TenantDetail](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-beta&preserve-view=true)  <br>v1.0 - [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization) |  |
| [TrustedCasForPasswordAuth](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - [certificateBasedAuthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthconfiguration)  <br>v1.0 - [certificateBasedAuthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthconfiguration) |  |
| [UserIdentity](https://learn.microsoft.com/en-us/previous-versions/azure/ad/graph/api/entity-and-complex-type-reference) | beta - [objectIdentity](https://learn.microsoft.com/en-us/graph/api/resources/objectidentity?view=graph-rest-beta&preserve-view=true)  <br>v1.0 - [objectIdentity](https://learn.microsoft.com/en-us/graph/api/resources/objectidentity) | New modeling for the identifiers used to sign into a user account, called **objectIdentity**. Supports Azure AD B2C scenarios. |

## Next step

[Review the migration checklist again](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist)
