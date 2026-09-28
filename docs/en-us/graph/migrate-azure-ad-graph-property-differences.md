<!-- Source: https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-property-differences -->
<!-- Sitemap-Last-Modified: 2025-03-17 -->

# Property differences between Azure AD Graph and Microsoft Graph

> This article is part of *Step 1: review API differences* in the [Azure AD Graph app migration planning checklist](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist) series.

This article compares Azure Active Directory \(Azure AD\) Graph to Microsoft Graph by highlighting the property differences between resources. Understanding these differences will help you update your code during migration.

If a property isn't mentioned in this article, it's already available in the [v1.0 version](https://learn.microsoft.com/en-us/graph/api/overview) of Microsoft Graph, with exactly the same name as in Azure AD Graph.

Because the [user](#user-property-differences) and [group](#group-property-differences) resources are frequently used, they're listed first. Other resources are listed alphabetically.

The underlying metadata for the services are accessible through these endpoints:

- [Azure AD Graph metadata](https://graph.windows.net/microsoft.com/$metadata?api-version=1.6)
- [Microsoft Graph beta metadata](https://graph.microsoft.com/beta/$metadata)
- [Microsoft Graph v1.0 metadata](https://graph.microsoft.com/v1.0/$metadata)

## User property differences

The Azure AD Graph **User** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **user** and inherits from **directoryObject**.

The Microsoft Graph v1.0 endpoint returns a limited set of user properties by default, while Azure AD Graph returns all properties. To read other properties not returned by default, specify them in a `$select` query. For more information, see the [user resource type](https://learn.microsoft.com/en-us/graph/api/resources/user).

The following table lists more property differences.

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **deletedTimestamp** | beta - **deletedDateTime**  <br>v1.0 - **deletedDateTime** |  |
| **dirSyncEnabled** | beta - **onPremisesSyncEnabled**  <br>v1.0 - **onPremisesSyncEnabled** |  |
| **facsimileTelephoneNumber** | beta - **faxNumber**  <br>v1.0 - **faxNumber** |  |
| **immutableId** | beta - **onPremisesImmutableId**  <br>v1.0 - **onPremisesImmutableId** |  |
| **isCompromised** | beta - *Not available*  <br>v1.0 - *Not available* | The Microsoft Graph [identity protection](https://learn.microsoft.com/en-us/graph/api/resources/identityprotection-overview) APIs provide more risk detection functionality. |
| **lastDirSyncDateTime** | beta - **onPremisesLastSyncDateTime**  <br>v1.0 - **onPremisesLastSyncDateTime** |  |
| **mobile** | beta - **mobilePhone**  <br>v1.0 - **mobilePhone** |  |
| **passwordProfile/enforceChangePasswordPolicy** | beta - **passwordProfile/forceChangePasswordNextSignIn**  <br>v1.0 - **passwordProfile/forceChangePasswordNextSignIn** |  |
| **passwordProfile/forceChangePasswordNextLogin** | beta - **passwordProfile/forceChangePasswordNextSignInWithMfa**  <br>v1.0 - **passwordProfile/forceChangePasswordNextSignInWithMfa** |  |
| **provisioningErrors** | beta - *Not available*  <br>v1.0 - *Not available* | This property and its information are deprecated. However, a new property describing any AD Connect-related provisioning errors can be found in **onPremisesProvisioningErrors** property. |
| **refreshTokensValidFromDateTime** | beta - **signinSessionsValidFromDateTime**  <br>v1.0 - **signinSessionsValidFromDateTime** |  |
| **signinNames** | beta - **identities/signInType**  <br>v1.0 - **identities/signInType** | This property is now part of the [objectIdentity](https://learn.microsoft.com/en-us/graph/api/resources/objectIdentity) resource. |
| **telephoneNumber** | beta - **businessPhones**  <br>v1.0 - **businessPhones** |  |
| **thumbnailPhoto** | beta - **photo**, photos  <br>v1.0 - **photo**, photos | The Microsoft Entra thumbnail photo isn't available through Microsoft Graph. Use the [photo API](https://learn.microsoft.com/en-us/graph/api/resources/profilephoto) instead. |
| **userIdentities** | beta - **identities**  <br>v1.0 - **identities** | For more information, see [objectIdentity](https://learn.microsoft.com/en-us/graph/api/resources/objectIdentity) resource type. |
| **userState** | beta - **externalUserState**  <br>v1.0 - **externalUserState** |  |
| **userStateChangedOn** | beta - **externalUserStateChangeDateTime**  <br>v1.0 - **externalUserStateChangeDateTime** |  |

## Group property differences

The Azure AD Graph **Group** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **group** and inherits from **directoryObject**. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **dirSyncEnabled** | beta - **onPremisesSyncEnabled**  <br>v1.0 - **onPremisesSyncEnabled** |  |
| **lastDirSyncDateTime** | beta - **onPremisesLastSyncDateTime**  <br>v1.0 - **onPremisesLastSyncDateTime** |  |
| **provisioningErrors** | beta - *Not available*  <br>v1.0 - *Not available* | This property and its information are deprecated. However, a new property describing any AD Connect-related provisioning errors can be found in **onPremisesProvisioningErrors** property. |

## Application property differences

The Azure AD Graph **Application** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **application** and inherits from **directoryObject**. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **acceptMappedClaims** | beta - **api/acceptMappedClaims**  <br>v1.0 - **api/acceptMappedClaims** | **acceptMappedClaims** is now part of the new [apiApplication](https://learn.microsoft.com/en-us/graph/api/resources/apiapplication) resource. |
| **availableToOtherTenants** | beta - **signInAudience**  <br>v1.0 - **signInAudience** | The default value in Azure AD Graph is `false` \(meaning `AzureADMyOrg`\) while for in Microsoft Graph is `AzureADandPersonalMicrosoftAccount`. |
| **errorUrl** | beta - *not available*  <br>v1.0 - *not available* | This property is deprecated. |
| **homepage** | beta - **web/homePageUrl**  <br>v1.0 - **web/homePageUrl** | The property is now part of the new [webApplication](https://learn.microsoft.com/en-us/graph/api/resources/webapplication) resource. |
| **informationalUrls** | beta - **info**  <br>v1.0 - **info** |  |
| **knownClientApplications** | beta - **api/knownClientApplications**  <br>v1.0 - **api/knownClientApplications** | The collection is now part of the new [apiApplication](https://learn.microsoft.com/en-us/graph/api/resources/apiapplication) resource. |
| **logoutUrl** | beta - **web/logoutUrl**  <br>v1.0 - **web/logoutUrl** | The property is now part of the [webApplication](https://learn.microsoft.com/en-us/graph/api/resources/webapplication) resource. |
| **logoUrl** | beta - **info/logoUrl**  <br>v1.0 - **info/logoUrl** | The property is now part of the new [informationalUrl](https://learn.microsoft.com/en-us/graph/api/resources/informationalurl) resource. |
| **mainLogo** | beta - **logo**  <br>v1.0 - **logo** |  |
| **oauth2AllowIdTokenImplicitFlow** | beta - **web/implicitGrantSettings/enableIdTokenIssuance**  <br>v1.0 - **web/implicitGrantSettings/enableIdTokenIssuance** | Renamed, and now part of the new [implicitGrantSettings](https://learn.microsoft.com/en-us/graph/api/resources/implicitgrantsettings) resource. |
| **oauth2AllowImplicitFlow** | beta - **web/implicitGrantSettings/enableAccessTokenIssuance**  <br>v1.0 - **web/implicitGrantSettings/enableAccessTokenIssuance** | Renamed, and now part of the new [implicitGrantSettings](https://learn.microsoft.com/en-us/graph/api/resources/implicitgrantsettings) resource. |
| **oauth2AllowUrlPathMatching** | beta - *not available*  <br>v1.0 - *not available* | This property is deprecated. |
| **oauth2Permissions** | beta - **api/oauth2PermissionScopes**  <br>v1.0 - **api/oauth2PermissionScopes** | Renamed and now part of the new [apiApplication](https://learn.microsoft.com/en-us/graph/api/resources/apiapplication) resource. |
| **publicClient** | beta - **isFallbackPublicClient**  <br>v1.0 - **isFallbackPublicClient** | This property now has a new meaning - it contains the public client settings like **redirectUris**. Microsoft Entra ID determines whether the app is a public or confidential client or not, with the **isFallbackPublicClient** property handling the one special case that Microsoft Entra ID can't determine automatically. |
| **recordConsentConditions** | beta - *not available*  <br>v1.0 - *not available* | This property is deprecated. |
| **replyUrls** | beta - **web/redirectUris**, **publicClient/redirectUris**  <br>v1.0 - **web/redirectUris**, **publicClient/redirectUris** | And being renamed, **redirectUris** is now part of the new [webApplication](https://learn.microsoft.com/en-us/graph/api/resources/webApplication) and [publicClient](https://learn.microsoft.com/en-us/graph/api/resources/publicClientApplication) complex types. This grouping allows developers to use specific URIs for their web and public clients \(such as an installed application on a desktop device\). |
| **samlMetadataUrl** | beta - **samlMetadataUrl**  <br>v1.0 - *Not yet available* |  |
| **serviceEndpoints** | beta - *Not available*  <br>v1.0 - *Not available* | This property is deprecated, but is available in the servicePrincipal entity. |

## AppRoleAssignment differences

The Azure AD Graph **AppRoleAssignment** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **appRoleAssignment** and inherits from **directoryObject**. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **creationTimestamp** | beta - **creationTimestamp**  <br>v1.0 - **createdDateTime** |  |
| **id** | beta - **appRoleId**  <br>v1.0 - **appRoleId** |  |

## Contact property differences

The Azure AD Graph **Contact** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **orgContact** and inherits from **directoryObject**. The properties differ as follows.

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **city** | beta - **postalAddresses/city**  <br>v1.0 - **postalAddresses/city** | The **city** property is part of the [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress) resource. |
| **country** | beta - **postalAddresses/countryOrRegion**  <br>v1.0 - **postalAddresses/countryOrRegion** | The **countryOrRegion** property is part of the [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress) resource. |
| **dirSyncEnabled** | beta - **onPremisesSyncEnabled**  <br>v1.0 - **onPremisesSyncEnabled** |  |
| **facsimileTelephoneNumber** | beta - **phones/businessFax**  <br>v1.0 - **phones/businessFax** | Now part of the [phone](https://learn.microsoft.com/en-us/graph/api/resources/phone) resource that supports various phone types. |
| **physicalDeliveryOfficeName** | beta - **officeLocation**  <br>v1.0 - **officeLocation** |  |
| **postalCode** | beta - **postalAddresses/postalCode**  <br>v1.0 - **postalAddresses/postalCode** | The **postalCode** property is part of the [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress) resource. |
| **provisioningErrors** | beta - not available  <br>v1.0 - not available | This property and its information are deprecated. However, a new property describing any AD Connect-related provisioning errors is in the **onPremisesProvisioningErrors** property. |
| **sipProxyAddress** | beta - **imAddresses**  <br>v1.0 - **imAddresses** |  |
| **state** | beta - **postalAddresses/state**  <br>v1.0 - **postalAddresses/state** | The **state** property is part of the [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress) resource. |
| **streetAddress** | beta - **postalAddresses/street**  <br>v1.0 - **postalAddresses/street** | The **street** property is part of the [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress) resource. |
| **telephoneNumber** | beta - **phones/business**  <br>v1.0 - **phones/business** | Now part of the [phone](https://learn.microsoft.com/en-us/graph/api/resources/phone) resource that supports various phone types. |
| **thumbnailPhoto** | beta - *Not yet available*  <br>v1.0 - *Not yet available* |  |

## Contract property differences

The Azure AD Graph **Contract** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **contract** and inherits from **directoryObject**. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **customerContextId** | beta - **customerId**  <br>v1.0 - **customerId** |  |

## Device property differences

The Azure AD Graph **Device** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **device** and inherits from **directoryObject**. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **approximateLastLogonTimestamp** | beta - **approximateLastSignInDateTime**  <br>v1.0 - **approximateLastSignInDateTime** |  |
| **complianceExpiryTime** | beta - **complianceExpirationDateTime**  <br>v1.0 - **complianceExpirationDateTime** |  |
| **deviceObjectVersion** | beta - **deviceVersion**  <br>v1.0 - **deviceVersion** |  |
| **deviceOSType** | beta - **operatingSystem**  <br>v1.0 - **operatingSystem** |  |
| **deviceOSVersion** | beta - **operatingSystemVersion**  <br>v1.0 - **operatingSystemVersion** |  |
| **devicePhysicalIds** | beta - **physicalIds**  <br>v1.0 - **physicalIds** |  |
| **deviceTrustType** | beta - **trustType**  <br>v1.0 - **trustType** |  |
| **dirSyncEnabled** | beta - **onPremisesSyncEnabled**  <br>v1.0 - **onPremisesSyncEnabled** |  |
| **lastDirSyncTime** | beta - **onPremisesLastSyncDateTime**  <br>v1.0 - **onPremisesLastSyncDateTime** |  |

## DirectoryObject property differences

The Azure AD Graph **DirectoryObject** resource is **directoryObject** in Microsoft Graph. Changes to its properties are seen in other resources that inherit from **DirectoryObject**. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **deletionTimestamp** | beta - **deletedDateTime**  <br>v1.0 - **deletedDateTime** | While **deletionTimestamp** was a DateTime type, **deletedDateTime** is a DateTimeOffset type. |
| **objectId** | beta - **id**  <br>v1.0 - **id** | The **id** property in Microsoft Graph is inherited from the [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity) resource. |
| **objectType** | beta - *Not available*  <br>v1.0 - *Not available* | This property isn't used in Microsoft Graph. Instead, Microsoft Graph returns the **@odata.type** property but only for APIs that might return objects of different types or derived types. For example, the [List group members](https://learn.microsoft.com/en-us/graph/api/group-list-members) API might return members who are [users](https://learn.microsoft.com/en-us/graph/api/resources/user), [groups](https://learn.microsoft.com/en-us/graph/api/resources/group), [service principals](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal), [organizational contacts](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact), or [devices](https://learn.microsoft.com/en-us/graph/api/resources/device). For users, the **@odata.type** is `#microsoft.graph.user`. |

## DirectoryObjectReference property differences

The Azure AD Graph **DirectoryObjectReference** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **directoryObjectPartnerReference** and inherits from **directoryObject**. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **externalContextId** | beta - **externalPartnerTenantId**  <br>v1.0 - **externalPartnerTenantId** |  |

## Domain property differences

The Azure AD Graph **Domain** resource is **domain** in Microsoft Graph. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **name** | beta - **id**  <br>v1.0 - **id** | In Microsoft Graph, the **id** property contains the domain name; the `name` property doesn't exist. |
| **forceDeleteState** | beta - **state**  <br>v1.0 - **state** | In Azure AD Graph, there are separate **forceDelete** and domain **state** properties. In Microsoft Graph, the **state** property handles all domain states. |
| **isDefaultForCloudRedirections** | beta - *Not yet available*  <br>v1.0 - *Not yet available* |  |

## OAuth2PermissionsGrant property differences

The Azure AD Graph **OAuth2PermissionsGrant** resource is **oAuth2PermissionsGrant** in Microsoft Graph. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **expiryTime** | beta - **expiryTime**  <br>v1.0 - *Removed* | This property isn't used and is removed in Microsoft Graph v1.0. |
| **startTime** | beta - **startTime**  <br>v1.0 - *Removed* | This property isn't used and is removed in Microsoft Graph v1.0. |

## Policy property differences

In Microsoft Graph, there are named policy types \(such as **tokenIssuancePolicy** or **tokenLifetimePolicy**\) rather than a generic policy resource type. More details are available in the [policy overview](https://learn.microsoft.com/en-us/graph/api/resources/policy-overview).

## ServiceEndpoint property differences

The Azure AD Graph **ServiceEndpoint** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **endpoint** and inherits from **directoryObject**. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **serviceId** | beta - **providerId**  <br>v1.0 - **providerId** |  |
| **serviceName** | beta - **providerName**  <br>v1.0 - **providerName** |  |
| **resourceId** | beta - **providerResourceId**  <br>v1.0 - **providerResourceId** |  |

## ServicePrincipal property differences

The Azure AD Graph **ServicePrincipal** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **servicePrincipal** and inherits from **directoryObject**. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **appOwnerTenantId** | beta - **appOwnerOrganizationId**  <br>v1.0 - **appOwnerOrganizationId** | Renamed. |
| **informationalUrls** | beta - **info**  <br>v1.0 - **info** |  |
| **oauth2Permissions** | beta - **publishedPermissionScopes**  <br>v1.0 - **oauth2PermissionScopes** | Renamed. |
| **preferredTokenSigningKeyEndDateTime** | beta - *Not yet available*  <br>v1.0 - *Not yet available* |  |
| **signInAudience** | beta - *Not yet available*  <br>v1.0 - *Not yet available* |  |
| **serviceEndpoints** | beta - **endpoint**  <br>v1.0 - **endpoint** | Renamed. |

## TenantDetails property differences

The Azure AD Graph **TenantDetail** resource inherits from **DirectoryObject**. In Microsoft Graph, it's **organization** and inherits from **directoryObject**. The properties differ as follows:

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **companyLastDirSyncTime** | beta - **onPremisesLastSyncDateTime**  <br>v1.0 - **onPremisesLastSyncDateTime** |  |
| **dirSyncEnabled** | beta - **onPremisesSyncEnabled**  <br>v1.0 - **onPremisesSyncEnabled** |  |
| **provisioningErrors** | beta - *Not available*  <br>v1.0 - *Not available* | This property and its information are deprecated. |
| **telephoneNumber** | beta - **businessPhones**  <br>v1.0 - **businessPhones** |  |

## TrustedCasForPasswordlessAuth property differences

The Azure AD Graph **TrustedCasForPasswordlessAuth** resource is [certificateBasedAuthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthconfiguration). There are no property differences; however, there are differences in the **certificateAuthority** resource type used by the **certificateAuthorities** property.

### CertificateAuthorityInformation property differences

The Azure AD Graph **CertificateAuthorityInformation** is **certificateAuthority** in Microsoft Graph. The following are the property differences.

| Azure AD Graph  <br>\(v1.6\) property | Microsoft Graph  <br>property | Comments |
| --- | --- | --- |
| **authorityType** | beta - **isRootAuthority**  <br>v1.0 - **isRootAuthority** | This property's is now a Boolean. In Azure AD Graph, this property had to be set to either `RootAuthority` or `IntermediateAuthority`. In Microsoft Graph, setting the new property to `true` is equivalent to `RootAuthority`. |
| **crlDistributionPoint** | beta - **certificateRevocationListUrl**  <br>v1.0 - **certificateRevocationListUrl** |  |
| **deltaCrlDistributionPoint** | beta - **deltaCertificateRevocationListUrl**  <br>v1.0 - **deltaCertificateRevocationListUrl** |  |
| **trustedCertificate** | beta - **certificate**  <br>v1.0 - **deltaCertificateRevocationListUrl** |  |
| **trustedIssuer** | beta - **issuer**  <br>v1.0 - **issuer** |  |
| **trustedIssuerSki** | beta - **issuerSki**  <br>v1.0 - **issuerSki** |  |

## Next step

[Review the migration checklist again](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist)
