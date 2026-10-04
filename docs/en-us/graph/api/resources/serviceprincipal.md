<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-10 -->

# servicePrincipal resource type

Namespace: microsoft.graph

Represents an instance of an application in a directory. Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

The [agentIdentityBlueprintPrincipal](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprintprincipal?view=graph-rest-1.0) resource inherits from this object.

This resource supports using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a [delta](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delta?view=graph-rest-1.0) function. This resource is an open type that allows additional properties beyond those documented here.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list?view=graph-rest-1.0) | [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) collection | Retrieve a list of servicePrincipal objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-serviceprincipals?view=graph-rest-1.0) | [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) | Creates a new servicePrincipal object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-get?view=graph-rest-1.0) | [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) | Read properties and relationships of servicePrincipal object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-update?view=graph-rest-1.0) | [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) | Update servicePrincipal object. |
| [Upsert](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-upsert?view=graph-rest-1.0) | [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) | Create a new servicePrincipal if it doesn't exist, or update the properties of an existing servicePrincipal. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete?view=graph-rest-1.0) | None | Delete servicePrincipal object. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delta?view=graph-rest-1.0) | servicePrincipal collection | Get incremental changes for service principals. |
| [List created objects](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-createdobjects?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get a createdObject object collection. |
| [List owned objects](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-ownedobjects?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get an ownedObject object collection. |
| **Deleted items** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a list of recently deleted servicePrincipal objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Retrieve the properties of a recently deleted servicePrincipal object. |
| [Restore](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Restore a recently deleted servicePrincipal object. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete?view=graph-rest-1.0) | None | Permanently delete a servicePrincipal object. |
| **App role assignments** |  |  |
| [List appRoleAssignments](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get the app roles that this service principal is assigned. |
| [Add appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-approleassignments?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Assign an app role to this service principal. |
| [Remove appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-approleassignments?view=graph-rest-1.0) | None | Remove an app role assignment from this service principal. |
| [List appRoleAssignedTo](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-approleassignedto?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | Get the users, groups, and service principals assigned app roles for this service principal. |
| [Add appRoleAssignedTo](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-approleassignedto?view=graph-rest-1.0) | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | Assign an app role for this service principal to a user, group, or service principal. |
| [Remove appRoleAssignedTo](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-approleassignedto?view=graph-rest-1.0) | None | Remove an app role assignment for this service principal from a user, group, or service principal. |
| **Certificates and secrets** |  |  |
| [Add password](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addpassword?view=graph-rest-1.0) | [passwordCredential](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredential?view=graph-rest-1.0) | Add a strong password or secret to a servicePrincipal. |
| [Remove password](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-removepassword?view=graph-rest-1.0) | [passwordCredential](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredential?view=graph-rest-1.0) | Remove a password or secret from a servicePrincipal. |
| [Add key](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addkey?view=graph-rest-1.0) | [keyCredential](https://learn.microsoft.com/en-us/graph/api/resources/keycredential?view=graph-rest-1.0) | Add a key credential to a servicePrincipal. |
| [Remove key](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-removekey?view=graph-rest-1.0) | None | Remove a key credential from a servicePrincipal. |
| [Add token signing certificate](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-addtokensigningcertificate?view=graph-rest-1.0) | [selfSignedCertificate](https://learn.microsoft.com/en-us/graph/api/resources/selfsignedcertificate?view=graph-rest-1.0) | Add a self-signed certificate to the service principal. Mostly used to configure SAML-based SSO applications from the [Microsoft Entra gallery](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/tutorial-list). |
| **Delegated permission classifications** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-delegatedpermissionclassifications?view=graph-rest-1.0) | [delegatedPermissionClassification](https://learn.microsoft.com/en-us/graph/api/resources/delegatedpermissionclassification?view=graph-rest-1.0) collection | Get the permission classifications for delegated permissions exposed by this service principal. |
| [Add](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-delegatedpermissionclassifications?view=graph-rest-1.0) | [delegatedPermissionClassification](https://learn.microsoft.com/en-us/graph/api/resources/delegatedpermissionclassification?view=graph-rest-1.0) | Add a permission classification for a delegated permission exposed by this service principal. |
| [Remove](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-delegatedpermissionclassifications?view=graph-rest-1.0) | None | Remove a permission classification for a delegated permission exposed by this service principal. |
| **Delegated \(OAuth2\) permission grants** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-oauth2permissiongrants?view=graph-rest-1.0) | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) collection | Get the delegated permission grants authorizing this service principal to access an API on behalf of a signed-in user. |
| **Membership** |  |  |
| [List memberOf](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-memberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the groups that this service principal is a direct member of from the memberOf navigation property. |
| [List transitive member of](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-transitivememberof?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | List the groups that this service principal is a member of. This operation is transitive and includes the groups that this service principal is a nested member of. |
| [Check member groups](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmembergroups?view=graph-rest-1.0) | String collection | Check for membership in a specified list of groups. |
| [Check member objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-checkmemberobjects?view=graph-rest-1.0) | String collection | Check for membership in a specified list of group, directory role, or administrative unit objects. |
| [Get member groups](https://learn.microsoft.com/en-us/graph/api/directoryobject-getmembergroups?view=graph-rest-1.0) | String collection | Get the list of groups that this service principal is a member of. |
| [Get member objects](https://learn.microsoft.com/en-us/graph/api/directoryobject-getmemberobjects?view=graph-rest-1.0) | String collection | Get the list of groups, administrative units, and directory roles that this service principal is a member of. |
| **Owners** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-list-owners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the owners of a service principal. |
| [Add](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-post-owners?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Assign an owner to a service principal. Service principal owners can be users or other service principals. |
| [Remove](https://learn.microsoft.com/en-us/graph/api/serviceprincipal-delete-owners?view=graph-rest-1.0) | None | Remove an owner from a service principal. As a recommended best practice, service principals should have at least two owners. |

## Properties

Important

Specific usage of `$filter` and the `$search` query parameter is supported only when you use the **ConsistencyLevel** header set to `eventual` and `$count`. For more information, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries#service-principal-properties).

| Property | Type | Description |
| :--- | :--- | :--- |
| accountEnabled | Boolean | `true` if the service principal account is enabled; otherwise, `false`. If set to `false`, then no users are able to sign in to this app, even if they're assigned to it. Supports `$filter` \(`eq`, `ne`, `not`, `in`\). |
| addIns | [addIn](https://learn.microsoft.com/en-us/graph/api/resources/addin?view=graph-rest-1.0) collection | Defines custom behavior that a consuming service can use to call an app in specific contexts. For example, applications that can render file streams [may set the addIns property](https://learn.microsoft.com/en-us/onedrive/developer/file-handlers/?view=odsp-graph-online&preserve-view=true) for its "FileHandler" functionality. This lets services like Microsoft 365 call the application in the context of a document the user is working on. |
| alternativeNames | String collection | Used to retrieve service principals by subscription, identify resource group and full resource IDs for [managed identities](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview). Supports `$filter` \(`eq`, `not`, `ge`, `le`, `startsWith`\). |
| appDescription | String | The description exposed by the associated application. |
| appDisplayName | String | The display name exposed by the associated application. Maximum length is 256 characters. |
| appId | String | The unique identifier for the associated application \(its **appId** property\). Alternate key. Supports `$filter` \(`eq`, `ne`, `not`, `in`, `startsWith`\). |
| applicationTemplateId | String | Unique identifier of the [applicationTemplate](https://learn.microsoft.com/en-us/graph/api/resources/applicationtemplate?view=graph-rest-1.0). Supports `$filter` \(`eq`, `not`, `ne`\). Read-only. `null` if the service principal wasn't created from an application template. |
| appOwnerOrganizationId | Guid | Contains the tenant ID where the application is registered. This is applicable only to service principals backed by applications. Supports `$filter` \(`eq`, `ne`, `NOT`, `ge`, `le`\). |
| appRoleAssignmentRequired | Boolean | Specifies whether users or other service principals need to be granted an app role assignment for this service principal before users can sign in or apps can get tokens. The default value is `false`. Not nullable.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `NOT`\). |
| appRoles | [appRole](https://learn.microsoft.com/en-us/graph/api/resources/approle?view=graph-rest-1.0) collection | The roles exposed by the application that's linked to this service principal. For more information, see the **appRoles** property definition on the [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) entity. Not nullable.  <br>  <br>App roles and exposed delegated permission scopes \(**oauth2PermissionScopes**\) share a default limit of 700 permission definitions per service principal, including definitions inherited from the application and definitions added directly to the service principal. Enabled and disabled definitions both count. This limit counts definitions, not app role assignments. For counting rules, behavior for existing objects above the limit, and design guidance, see [App role limits](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#app-role-limits). |
| createdByAppId | String | The **appId** of the application that created this service principal. Set internally by Microsoft Entra ID. Read-only. |
| customSecurityAttributes | [customSecurityAttributeValue](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributevalue?view=graph-rest-1.0) | An open complex type that holds the value of a custom security attribute that is assigned to a directory object. Nullable.  <br>  <br>Requires `$select` to retrieve. Supports `$filter` \(`eq`, `ne`, `not`, `startsWith`\). Filter value is case sensitive.  <br><br><br><li>To read this property, the calling app must be assigned the <em>CustomSecAttributeAssignment.Read.All</em> permission. To write this property, the calling app must be assigned the <em>CustomSecAttributeAssignment.ReadWrite.All</em> permissions. </li><br><br><li>To read or write this property in delegated scenarios, the admin must be assigned the <em>Attribute Assignment Administrator</em> role.</li> |
| deletedDateTime | DateTimeOffset | The date and time the service principal was deleted. Read-only. |
| description | String | Free text field to provide an internal end-user facing description of the service principal. End-user portals such [MyApps](https://learn.microsoft.com/en-us/azure/active-directory/user-help/my-apps-portal-end-user-access) displays the application description in this field. The maximum allowed size is 1,024 characters. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `startsWith`\) and `$search`. |
| disabledByMicrosoftStatus | String | Specifies whether Microsoft has disabled the registered application. The possible values are: `null` \(default value\), `NotDisabled`, and `DisabledDueToViolationOfServicesAgreement` \(reasons include suspicious, abusive, or malicious activity, or a violation of the Microsoft Services Agreement\).  <br>  <br>Supports `$filter` \(`eq`, `ne`, `not`\). |
| displayName | String | The display name for the service principal. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` on `null` values\), `$search`, and `$orderby`. |
| homepage | String | Home page or landing page of the application. |
| id | String | The unique identifier for the service principal. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). Key. Not nullable. Read-only. Supports `$filter` \(`eq`, `ne`, `not`, `in`\). |
| info | [informationalUrl](https://learn.microsoft.com/en-us/graph/api/resources/informationalurl?view=graph-rest-1.0) | Basic profile information of the acquired application such as app's marketing, support, terms of service and privacy statement URLs. The terms of service and privacy statement are surfaced to users through the user consent experience. For more info, see How to: [Add Terms of service and privacy statement for registered Microsoft Entra apps](https://learn.microsoft.com/en-us/azure/active-directory/develop/howto-add-terms-of-service-privacy-statement).  <br>  <br>Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, and `eq` on `null` values\). |
| keyCredentials | [keyCredential](https://learn.microsoft.com/en-us/graph/api/resources/keycredential?view=graph-rest-1.0) collection | The collection of key credentials associated with the service principal. Not nullable. Supports `$filter` \(`eq`, `not`, `ge`, `le`\). |
| loginUrl | String | Specifies the URL where the service provider redirects the user to Microsoft Entra ID to authenticate. Microsoft Entra ID uses the URL to launch the application from Microsoft 365 or the Microsoft Entra My Apps. When blank, Microsoft Entra ID performs IdP-initiated sign-on for applications configured with [SAML-based single sign-on](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/what-is-single-sign-on#saml-sso). The user launches the application from Microsoft 365, the Microsoft Entra My Apps, or the Microsoft Entra SSO URL. |
| logoutUrl | String | Specifies the URL that the Microsoft's authorization service uses to sign out a user using OpenID Connect [front-channel](https://openid.net/specs/openid-connect-frontchannel-1_0.html), [back-channel](https://openid.net/specs/openid-connect-backchannel-1_0.html), or SAML sign out protocols. |
| notes | String | Free text field to capture information about the service principal, typically used for operational purposes. Maximum allowed size is 1,024 characters. |
| notificationEmailAddresses | String collection | Specifies the list of email addresses where Microsoft Entra ID sends a notification when the active certificate is near the expiration date. This is only for the certificates used to sign the SAML token issued for Microsoft Entra Gallery applications. |
| oauth2PermissionScopes | [permissionScope](https://learn.microsoft.com/en-us/graph/api/resources/permissionscope?view=graph-rest-1.0) collection | The delegated permissions exposed by the application. For more information, see the **oauth2PermissionScopes** property on the [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) entity's **api** property. Not nullable.  <br>  <br>These scopes and **appRoles** share a default limit of 700 permission definitions per service principal. Enabled and disabled definitions both count. For counting rules, behavior for existing objects above the limit, and design guidance, see [App role limits](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#app-role-limits). |
| passwordCredentials | [passwordCredential](https://learn.microsoft.com/en-us/graph/api/resources/passwordcredential?view=graph-rest-1.0) collection | The collection of password credentials associated with the application. Not nullable. |
| preferredSingleSignOnMode | string | Specifies the single sign-on mode configured for this application. Microsoft Entra ID uses the preferred single sign-on mode to launch the application from Microsoft 365 or the My Apps portal. The supported values are `password`, `saml`, `notSupported`, and `oidc`. **Note:** This field might be `null` for older SAML apps and for OIDC applications where it isn't set automatically. |
| preferredTokenSigningKeyThumbprint | String | This property can be used on SAML applications \(apps that have **preferredSingleSignOnMode** set to `saml`\) to control which certificate is used to sign the SAML responses. For applications that aren't SAML, don't write or otherwise rely on this property. |
| replyUrls | String collection | The URLs that user tokens are sent to for sign in with the associated application, or the redirect URIs that OAuth 2.0 authorization codes and access tokens are sent to for the associated application. Not nullable. |
| resourceSpecificApplicationPermissions | [resourceSpecificPermission](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermission?view=graph-rest-1.0) collection | The resource-specific application permissions exposed by this application. Currently, resource-specific permissions are only supported for [Teams apps accessing to specific chats and teams](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent) using Microsoft Graph. Read-only. |
| samlSingleSignOnSettings | [samlSingleSignOnSettings](https://learn.microsoft.com/en-us/graph/api/resources/samlsinglesignonsettings?view=graph-rest-1.0) | The collection for settings related to saml single sign-on. |
| servicePrincipalNames | String collection | Contains the list of **identifiersUris**, copied over from the associated [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0). Additional values can be added to hybrid applications. These values can be used to identify the permissions exposed by this app within Microsoft Entra ID. For example,<br><br>- Client apps can specify a resource URI that is based on the values of this property to acquire an access token, which is the URI returned in the "aud" claim.<br><br>  <br>The any operator is required for filter expressions on multi-valued properties. Not nullable.  <br>  <br>Supports `$filter` \(`eq`, `not`, `ge`, `le`, `startsWith`\). |
| servicePrincipalType | String | Identifies whether the service principal represents an application, a managed identity, or a legacy application. This property is set by Microsoft Entra ID internally. The **servicePrincipalType** property can be set to three different values:<br><br>- `Application` - A service principal that represents an application or service. The **appId** property identifies the associated app registration, and matches the **appId** of an [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0), possibly from a different tenant. If the associated app registration is missing, tokens aren't issued for the service principal.<br>- `ManagedIdentity` - A service principal that represents a [managed identity](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview). Service principals representing managed identities can be granted access and permissions, but can't be updated or modified directly.<br>- `Legacy` - A service principal that represents an app created before app registrations, or through legacy experiences. A legacy service principal can have credentials, service principal names, reply URLs, and other properties that are editable by an authorized user, but doesn't have an associated app registration. The **appId** value doesn't associate the service principal with an app registration. The service principal can only be used in the tenant where it was created.<br>- `ServiceIdentity` - A service principal that represents an [agent identity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity).<br><br><li><code>SocialIdp</code> - For internal use. </li> |
| signInAudience | String | Specifies the Microsoft accounts that are supported for the current application. Read-only.  <br>  <br>Supported values are:<br><br>- `AzureADMyOrg`: Users with a Microsoft work or school account in my organization's Microsoft Entra tenant \(single-tenant\).<br>- `AzureADMultipleOrgs`: Users with a Microsoft work or school account in any organization's Microsoft Entra tenant \(multitenant\).<br>- `AzureADandPersonalMicrosoftAccount`: Users with a personal Microsoft account, or a work or school account in any organization's Microsoft Entra tenant.<br>- `PersonalMicrosoftAccount`: Users with a personal Microsoft account only. |
| tags | String collection | Custom strings that can be used to categorize and identify the service principal. Not nullable. The value is the union of strings set here and on the associated [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) entity's **tags** property.  <br>  <br>Supports `$filter` \(`eq`, `not`, `ge`, `le`, `startsWith`\). |
| tokenEncryptionKeyId | String | Specifies the keyId of a public key from the keyCredentials collection. When configured, Microsoft Entra ID issues tokens for this application encrypted using the key specified by this property. The application code that receives the encrypted token must use the matching private key to decrypt the token before it can be used for the signed-in user. |
| verifiedPublisher | [verifiedPublisher](https://learn.microsoft.com/en-us/graph/api/resources/verifiedpublisher?view=graph-rest-1.0) | Specifies the verified publisher of the application that's linked to this service principal. |

## Relationships

Important

Specific usage of the `$filter` query parameter is supported only when you use the **ConsistencyLevel** header set to `eventual` and `$count`. For more information, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries#user-properties).

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appManagementPolicies | [appManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appmanagementpolicy?view=graph-rest-1.0) collection | The appManagementPolicy applied to this application. |
| appRoleAssignedTo | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) | App role assignments for this app or service, granted to users, groups, and other service principals. Supports `$expand`. |
| appRoleAssignments | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment?view=graph-rest-1.0) collection | App role assignment for another app or service, granted to this service principal. Supports `$expand`. |
| claimsMappingPolicies | [claimsMappingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/claimsmappingpolicy?view=graph-rest-1.0) collection | The claimsMappingPolicies assigned to this service principal. Supports `$expand`. |
| createdObjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects created by this service principal. Read-only. Nullable. |
| federatedIdentityCredentials | [federatedIdentityCredential](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredential?view=graph-rest-1.0) collection | Federated identities for a specific type of service principal - managed identity. Supports `$expand` and `$filter` \(`/$count eq 0`, `/$count ne 0`\). |
| homeRealmDiscoveryPolicies | [homeRealmDiscoveryPolicy](https://learn.microsoft.com/en-us/graph/api/resources/homerealmdiscoverypolicy?view=graph-rest-1.0) collection | The homeRealmDiscoveryPolicies assigned to this service principal. Supports `$expand`. |
| memberOf | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Roles that this service principal is a member of. HTTP Methods: GET Read-only. Nullable. Supports `$expand`. |
| oauth2PermissionGrants | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant?view=graph-rest-1.0) collection | Delegated permission grants authorizing this service principal to access an API on behalf of a signed-in user. Read-only. Nullable. |
| ownedObjects | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects that this service principal owns. Read-only. Nullable. Supports `$expand`, `$select` nested in `$expand`, and `$filter` \(`/$count eq 0`, `/$count ne 0`, `/$count eq 1`, `/$count ne 1`\). |
| owners | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Directory objects that are owners of this servicePrincipal. The owners are a set of nonadmin users or servicePrincipals who are allowed to modify this object. Supports `$expand`, `$filter` \(`/$count eq 0`, `/$count ne 0`, `/$count eq 1`, `/$count ne 1`\), and `$select` nested in `$expand`. |
| remoteDesktopSecurityConfiguration | [remoteDesktopSecurityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/remotedesktopsecurityconfiguration?view=graph-rest-1.0) | The remoteDesktopSecurityConfiguration object applied to this service principal. Supports `$filter` \(`eq`\) for **isRemoteDesktopProtocolEnabled** property. |
| synchronization | [synchronization](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronization?view=graph-rest-1.0) | Represents the capability for Microsoft Entra identity synchronization through the Microsoft Graph API. |
| tokenIssuancePolicies | [tokenIssuancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenissuancepolicy?view=graph-rest-1.0) collection | The tokenIssuancePolicies assigned to this service principal. |
| tokenLifetimePolicies | [tokenLifetimePolicy](https://learn.microsoft.com/en-us/graph/api/resources/tokenlifetimepolicy?view=graph-rest-1.0) collection | The tokenLifetimePolicies assigned to this service principal. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "accountEnabled": true,
  "addIns": [{"@odata.type": "microsoft.graph.addIn"}],
  "alternativeNames": ["String"] ,
  "appDisplayName": "String",
  "appId": "String",
  "appOwnerOrganizationId": "Guid",
  "appRoleAssignmentRequired": true,
  "appRoles": [{"@odata.type": "microsoft.graph.appRole"}],
  "createdByAppId": "String",
  "customSecurityAttributes": {
    "@odata.type": "microsoft.graph.customSecurityAttributeValue"
  },
  "disabledByMicrosoftStatus": "String",
  "displayName": "String",
  "homepage": "String",
  "id": "String (identifier)",
  "info": {"@odata.type": "microsoft.graph.informationalUrl"},
  "keyCredentials": [{"@odata.type": "microsoft.graph.keyCredential"}],
  "logoutUrl": "String",
  "notes": "String",
  "oauth2PermissionScopes": [{"@odata.type": "microsoft.graph.permissionScope"}],
  "passwordCredentials": [{"@odata.type": "microsoft.graph.passwordCredential"}],
  "preferredTokenSigningKeyThumbprint": "String",
  "replyUrls": ["String"],
  "resourceSpecificApplicationPermissions": [{"@odata.type": "microsoft.graph.resourceSpecificPermission"}],
  "servicePrincipalNames": ["String"],
  "servicePrincipalType": "String",
  "tags": ["String"],
  "tokenEncryptionKeyId": "String",
  "verifiedPublisher": {"@odata.type": "microsoft.graph.verifiedPublisher"}
}
```
