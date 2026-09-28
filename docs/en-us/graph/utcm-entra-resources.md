<!-- Source: https://learn.microsoft.com/en-us/graph/utcm-entra-resources -->
<!-- Sitemap-Last-Modified: 2026-01-29 -->

# Supported Microsoft Entra resources for Tenant Configuration Management

This article lists the supported resource types for Microsoft Entra in the Tenant Configuration Management \(TCM\) APIs in Microsoft Graph. Use these resource types to monitor and manage your Microsoft Entra configuration settings.

For the complete schema, required permissions, and examples for each resource type, see the [TCM schema store](https://json.schemastore.org/utcm-monitor.json).

## administrativeUnit resource type

#### Description

This resource configures an Microsoft Entra Administrative Unit.

#### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | DisplayName of the Administrative Unit | - |
| Id | Write | String | Object-Id of the Administrative Unit | - |
| Description | Write | String | Description of the Administrative Unit | - |
| Visibility | Write | String | Visibility of the Administrative Unit. Specify HiddenMembership if members of the AU are hidden | - |
| MembershipType | Write | String | Specify membership type. Possible values are Assigned and Dynamic. The functionality is currently in preview. | - |
| MembershipRule | Write | String | Specify membership rule. Requires that MembershipType is set to Dynamic. The functionality is currently in preview. | - |
| MembershipRuleProcessingState | Write | String | Specify dynamic membership-rule processing-state. Valid values are 'On' and 'Paused'. Requires that MembershipType is set to Dynamic. The functionality is currently in preview. | - |
| Members | Write | MSFT\_MicrosoftGraphMember\[\] | Specify members. Only specify if MembershipType is NOT set to Dynamic | - |
| ScopedRoleMembers | Write | MSFT\_MicrosoftGraphScopedRoleMembership\[\] | Specify Scoped Role Membership. Note: Any groups must be role-enabled | - |
| Ensure | Write | String | Present ensures the Administrative Unit exists, absent ensures it's removed. | `Present`, `Absent` |

##### MSFT\_MicrosoftGraphMember

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identity | Write | String | Identity of member. For users, specify a UserPrincipalName. For groups, devices and service principals, specify DisplayName | - |
| Type | Write | String | Specify User, Group, or Device to interpret the identity for Members. Specify User, Group, or ServicePrincipal for ScopedRoleMembers. | `User`, `Group`, `Device`, `ServicePrincipal` |

##### MSFT\_MicrosoftGraphScopedRoleMembership

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| RoleName | Write | String | Name of the Microsoft Entra Role that is assigned. See [Roles that can be assigned with administrative unit scope](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal?tabs=admin-center#roles-that-can-be-assigned-with-administrative-unit-scope) | - |
| RoleMemberInfo | Write | MSFT\_MicrosoftGraphMember | Member that is assigned to the scoped role. Note: Any groups must be role-enabled | - |

#### Permissions

##### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Privileged Role Administrator |

##### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | AdministrativeUnit.Read.All, RoleManagement.Read.Directory |
| Update | AdministrativeUnit.ReadWrite.All, Application.Read.All, Device.Read.All, Group.Read.All, RoleManagement.Read.Directory, User.Read.All |

## application resource type

### Description

This resource configures an Microsoft Entra Application.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | DisplayName of the app | - |
| ObjectId | Write | String | ObjectID of the app. | - |
| AppId | Write | String | AppId for the app. | - |
| AvailableToOtherTenants | Write | Boolean | Indicates whether this application is available in other tenants. | - |
| Description | Write | String | A free text field to provide a description of the application object to end users. The maximum allowed size is 1,024 characters. | - |
| GroupMembershipClaims | Write | String | A bitmask that configures the groups claim issued in a user or OAuth 2.0 access token that the application expects. | - |
| Homepage | Write | String | The URL to the application's homepage. | - |
| IdentifierUris | Write | StringArray\[\] | User-defined URIs that uniquely identify a Web application within its Microsoft Entra tenant, or within a verified custom domain. | - |
| IsFallbackPublicClient | Write | Boolean | Specifies the fallback application type as public client, such as an installed application running on a mobile device. The default value is false, which means the fallback application type is confidential client such as web app. There are certain scenarios where Microsoft Entra ID can't determine the client application type. For example, ROPC flow where it is configured without specifying a redirect URI. In those cases, Microsoft Entra ID interprets the application type based on the value of this property. | - |
| KnownClientApplications | Write | StringArray\[\] | Client applications that are tied to this resource application. | - |
| LogoutURL | Write | String | The logout url for this application. | - |
| PublicClient | Write | Boolean | Specifies whether this application is a public client \(such as an installed application running on a mobile device\). Default is false. | - |
| ReplyURLs | Write | StringArray\[\] | Specifies the URLs that user tokens are sent to for sign in, or the redirect URIs that OAuth 2.0 authorization codes and access tokens are sent to. | - |
| Owners | Write | StringArray\[\] | UPN or ObjectID values of the app's owners. | - |
| Ensure | Write | String | Specify if the Microsoft Entra App should exist or not. | `Present`, `Absent` |
| Permissions | Write | ApplicationPermission\[\] | API permissions for the Microsoft Entra Application. | - |

#### ApplicationPermission

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Name | Write | String | Name of the requested permission. | - |
| SourceAPI | Write | String | Name of the API from which the permission comes from. | - |
| Type | Write | String | Type of permission. | `AppOnly`, `Delegated` |
| AdminConsentGranted | Write | Boolean | Represents whether or not the Admin consent has been granted on the app. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | None |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Application.Read.All, Policy.Read.All |
| Update | Application.ReadWrite.All, User.Read.All |

## authenticationContextClassReference resource type

### Description

Represents a Microsoft Entra authentication context class reference. Authentication context class references are custom values that define a Conditional Access authentication requirement

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Key | String | Identifier used to reference the authentication context class. The id is used to trigger step-up authentication for the referenced authentication requirements and is the value that is issued in the ACRS \(Authentication Context Class Reference\) claim of an access token. This value in the claim is used to verify that the required authentication context is satisfied. The allowed values are c1 through c25. | `c1`, `c2`, `c3`, `c4`, `c5`, `c6`, `c7`, `c8`, `c9`, `c10`, `c11`, `c12`, `c13`, `c14`, `c15`, `c16`, `c17`, `c18`, `c19`, `c20`, `c21`, `c22`, `c23`, `c24`, `c25` |
| DisplayName | Write | String | A friendly name that identifies the authenticationContextClassReference object when building user-facing admin experiences. For example, a selection UX | - |
| Description | Write | String | A short explanation of the policies that are enforced by authenticationContextClassReference. This value should be used to provide secondary text to describe the authentication context class reference when building user-facing admin experiences. For example, a selection UX. | - |
| IsAvailable | Write | Boolean | Indicates whether the authenticationContextClassReference is published by the security admin and is ready for use by apps. When it's set to false, it shouldn't be shown in admin UX experiences because the value isn't currently available for selection. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.ConditionalAccess |
| Update | Policy.ReadWrite.ConditionalAccess |

## authenticationMethodPolicy resource type

### Description

Microsoft Entra Authentication Method Policy

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Description | Write | String | A description of the policy. | - |
| DisplayName | Key | String | The name of the policy. | - |
| PolicyMigrationState | Write | String | The state of migration of the authentication methods policy from the legacy multifactor authentication and self-service password reset \(SSPR\) policies. The possible values are: premigration - means the authentication methods policy is used for authentication only, legacy policies are respected. migrationInProgress - means the authentication methods policy is used for both authentication and SSPR, legacy policies are respected. migrationComplete - means the authentication methods policy is used for authentication and SSPR, legacy policies are ignored. unknownFutureValue - Evolvable enumeration sentinel value. Don't use. | `preMigration`, `migrationInProgress`, `migrationComplete`, `unknownFutureValue` |
| PolicyVersion | Write | String | The version of the policy in use. | - |
| ReconfirmationInDays | Write | UInt32 | Days before the user is asked to reconfirm their method. | - |
| RegistrationEnforcement | Write | MSFT\_MicrosoftGraphregistrationEnforcement | Enforce registration at sign-in time. This property can be used to remind users to set up targeted authentication methods. | - |
| SystemCredentialPreferences | Write | MSFT\_MicrosoftGraphsystemCredentialPreferences | Prompt users with their most-preferred credential for multifactor authentication. | - |
| Id | Write | String | The unique identifier for an entity. Read-only. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present` |

#### MSFT\_MicrosoftGraphRegistrationEnforcement

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AuthenticationMethodsRegistrationCampaign | Write | MSFT\_MicrosoftGraphAuthenticationMethodsRegistrationCampaign | Run campaigns to remind users to set up targeted authentication methods. | - |

#### MSFT\_MicrosoftGraphAuthenticationMethodsRegistrationCampaign

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ExcludeTargets | Write | MSFT\_MicrosoftGraphExcludeTarget\[\] | Users and groups of users that are excluded from being prompted to set up the authentication method. | - |
| IncludeTargets | Write | MSFT\_MicrosoftGraphAuthenticationMethodsRegistrationCampaignIncludeTarget\[\] | Users and groups of users that are prompted to set up the authentication method. | - |
| SnoozeDurationInDays | Write | UInt32 | Specifies the number of days that the user sees a prompt again if they select 'Not now' and snoozes the prompt. Minimum 0 days. Maximum: 14 days. If the value is '0', the user is prompted during every MFA attempt. | - |
| State | Write | String | Enable or disable the feature. Possible values are: default, enabled, disabled, unknownFutureValue. The default value is used when the configuration isn't explicitly set and uses the default behavior of Microsoft Entra for the setting. The default value is disabled. | `default`, `enabled`, `disabled`, `unknownFutureValue` |

#### AuthenticationMethodPolicyExcludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

#### AuthenticationMethodPolicyIncludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The ID of the entity targeted. | - |
| TargetType | Write | String | The kind of entity targeted. Possible values are: user, group. | `user`, `group`, `unknownFutureValue` |

#### MSFT\_MicrosoftGraphExcludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra user or group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: user, group, unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

#### MSFT\_MicrosoftGraphAuthenticationMethodsRegistrationCampaignIncludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra user or group. | - |
| TargetedAuthenticationMethod | Write | String | The authentication method that the user is prompted to register. The value must be microsoftAuthenticator. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: user, group, unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

#### MSFT\_MicrosoftGraphSystemCredentialPreferences

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ExcludeTargets | Write | AuthenticationMethodPolicyExcludeTarget\[\] | Users and groups excluded from the preferred authentication method experience of the system. | - |
| IncludeTargets | Write | AuthenticationMethodPolicyIncludeTarget\[\] | Users and groups included in the preferred authentication method experience of the system. | - |
| State | Write | String | Indicates whether the feature is enabled or disabled. Possible values are: default, enabled, disabled, unknownFutureValue. The default value is used when the configuration isn't explicitly set, and uses the default behavior of Microsoft Entra for the setting. The default value is disabled. | `default`, `enabled`, `disabled`, `unknownFutureValue` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.AuthenticationMethod |
| Update | Policy.ReadWrite.AuthenticationMethod |

## authenticationMethodPolicyAuthenticator resource type

### Description

Microsoft Entra Authentication Method Policy Authenticator

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| FeatureSettings | Write | MSFT\_MicrosoftGraphMicrosoftAuthenticatorFeatureSettings | A collection of Microsoft Authenticator settings such as number matching and location context, and whether they're enabled for all users or specific users only. | - |
| IsSoftwareOathEnabled | Write | Boolean | true if users can use the OTP code generated by the Microsoft Authenticator app, false otherwise. | - |
| ExcludeTargets | Write | AuthenticationMethodPolicyAuthenticatorExcludeTarget\[\] | Displayname of the groups of users that are excluded from a policy. | - |
| IncludeTargets | Write | AuthenticationMethodPolicyAuthenticatorIncludeTarget\[\] | Displayname of the groups of users that are included from a policy. | - |
| State | Write | String | The state of the policy. Possible values are: enabled, disabled. | `enabled`, `disabled` |
| Id | Key | String | The unique identifier for an entity. Read-only. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_MicrosoftGraphMicrosoftAuthenticatorFeatureSettings

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| CompanionAppAllowedState | Write | MSFT\_MicrosoftGraphAuthenticationMethodFeatureConfiguration | Determines whether users are able to approve push notifications on other Microsoft applications such as Outlook Mobile. | - |
| DisplayAppInformationRequiredState | Write | MSFT\_MicrosoftGraphAuthenticationMethodFeatureConfiguration | Determines whether the user's Authenticator app shows them the client app they're signing into. | - |
| DisplayLocationInformationRequiredState | Write | MSFT\_MicrosoftGraphAuthenticationMethodFeatureConfiguration | Determines whether the user's Authenticator app shows them the geographic location of where the authentication request originated from. | - |
| NumberMatchingRequiredState | Write | MSFT\_MicrosoftGraphAuthenticationMethodFeatureConfiguration | Specifies whether the user needs to enter a number in the Authenticator app from the login screen to complete their login. Value is ignored for phone sign-in notifications. | - |

#### MSFT\_MicrosoftGraphAuthenticationMethodFeatureConfiguration

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ExcludeTarget | Write | AuthenticationMethodPolicyAuthenticatorFeatureTarget | A single entity excluded from using this feature. | - |
| IncludeTarget | Write | AuthenticationMethodPolicyAuthenticatorFeatureTarget | A single entity allowed to use this feature. | - |
| State | Write | String | Enable or disable the feature. Possible values are: default, enabled, disabled, unknownFutureValue. The default value is used when the configuration isn't explicitly set and uses the default behavior of Microsoft Entra for the setting. The default value is disabled. | `default`, `enabled`, `disabled`, `unknownFutureValue` |

#### AuthenticationMethodPolicyAuthenticatorFeatureTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The ID of the entity targeted in the include or exclude rule or all\_users to target all users. | - |
| TargetType | Write | String | The kind of entity targeted. The possible values are: group, administrativeUnit, role, unknownFutureValue. | `group`, `administrativeUnit`, `role`, `unknownFutureValue` |

#### AuthenticationMethodPolicyAuthenticatorExcludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

#### AuthenticationMethodPolicyAuthenticatorIncludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.AuthenticationMethod, Group.Read.All |
| Update | Policy.ReadWrite.AuthenticationMethod, Group.Read.All |

## authenticationMethodPolicyEmail resource type

### Description

Microsoft Entra Authentication Method Policy Email

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AllowExternalIdToUseEmailOtp | Write | String | Determines whether email OTP is usable by external users for authentication. Possible values are: default, enabled, disabled, unknownFutureValue. Tenants in the default state who didn't use public preview automatically has email OTP enabled beginning in October 2021. | `default`, `enabled`, `disabled`, `unknownFutureValue` |
| ExcludeTargets | Write | AuthenticationMethodPolicyEmailExcludeTarget\[\] | Displayname of the groups of users that are excluded from a policy. | - |
| IncludeTargets | Write | AuthenticationMethodPolicyEmailIncludeTarget\[\] | Displayname of the groups of users that are included from a policy. | - |
| State | Write | String | The state of the policy. Possible values are: enabled, disabled. | `enabled`, `disabled` |
| Id | Key | String | The unique identifier for an entity. Read-only. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures the policy is removed. | `Present`, `Absent` |

#### AuthenticationMethodPolicyEmailExcludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

#### AuthenticationMethodPolicyEmailIncludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.AuthenticationMethod, Group.Read.All |
| Update | Policy.ReadWrite.AuthenticationMethod, Group.Read.All |

## authenticationMethodPolicyFido2 resource type

### Description

Microsoft Entra Authentication Method Policy Fido2

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsAttestationEnforced | Write | Boolean | Determines whether attestation must be enforced for FIDO2 security key registration. | - |
| IsSelfServiceRegistrationAllowed | Write | Boolean | Determines if users can register new FIDO2 security keys. | - |
| KeyRestrictions | Write | MSFT\_MicrosoftGraphfido2KeyRestrictions | Controls whether key restrictions are enforced on FIDO2 security keys, either allowing or disallowing certain key types as defined by Authenticator Attestation GUID \(AAGUID\), an identifier that indicates the type \(e.g. make and model\) of the authenticator. | - |
| ExcludeTargets | Write | AuthenticationMethodPolicyFido2ExcludeTarget\[\] | Displayname of the groups of users that are excluded from a policy. | - |
| IncludeTargets | Write | AuthenticationMethodPolicyFido2IncludeTarget\[\] | Displayname of the groups of users that are included from a policy. | - |
| State | Write | String | The state of the policy. Possible values are: enabled, disabled. | `enabled`, `disabled` |
| Id | Key | String | The unique identifier for an entity. Read-only. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_MicrosoftGraphFido2KeyRestrictions

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AaGuids | Write | StringArray\[\] | A collection of Authenticator Attestation GUIDs. AADGUIDs define key types and manufacturers. | - |
| EnforcementType | Write | String | Enforcement type. Possible values are: allow, block. | `allow`, `block`, `unknownFutureValue` |
| IsEnforced | Write | Boolean | Determines if the configured key enforcement is enabled. | - |

#### AuthenticationMethodPolicyFido2ExcludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

#### AuthenticationMethodPolicyFido2IncludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.AuthenticationMethod, Group.Read.All |
| Update | Policy.ReadWrite.AuthenticationMethod, Group.Read.All |

## authenticationMethodPolicySms resource type

### Description

Microsoft Entra Authentication Method Policy SMS

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ExcludeTargets | Write | AuthenticationMethodPolicySmsExcludeTarget\[\] | Displayname of the groups of users that are excluded from a policy. | - |
| IncludeTargets | Write | AuthenticationMethodPolicySmsIncludeTarget\[\] | Displayname of the groups of users that are included from a policy. | - |
| State | Write | String | The state of the policy. Possible values are: enabled, disabled. | `enabled`, `disabled` |
| Id | Key | String | The unique identifier for an entity. Read-only. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures the policy is removed. | `Present`, `Absent` |

#### AuthenticationMethodPolicySmsExcludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

#### AuthenticationMethodPolicySmsIncludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.AuthenticationMethod, Group.Read.All |
| Update | Policy.ReadWrite.AuthenticationMethod, Group.Read.All |

## authenticationMethodPolicySoftware resource type

### Description

Microsoft Entra Authentication Method Policy Software

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ExcludeTargets | Write | AuthenticationMethodPolicySoftwareExcludeTarget\[\] | Displayname of the groups of users that are excluded from a policy. | - |
| IncludeTargets | Write | AuthenticationMethodPolicySoftwareIncludeTarget\[\] | Displayname of the groups of users that are included from a policy. | - |
| State | Write | String | The state of the policy. Possible values are: enabled, disabled. | `enabled`, `disabled` |
| Id | Key | String | The unique identifier for an entity. Read-only. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### AuthenticationMethodPolicySoftwareExcludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

#### AuthenticationMethodPolicySoftwareIncludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.AuthenticationMethod, Group.Read.All |
| Update | Policy.ReadWrite.AuthenticationMethod, Group.Read.All |

## authenticationMethodPolicyTemporary resource type

### Description

Microsoft Entra Authentication Method Policy Temporary

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DefaultLength | Write | UInt32 | Default length in characters of a Temporary Access Pass object. Must be between 8 and 48 characters. | - |
| DefaultLifetimeInMinutes | Write | UInt32 | Default lifetime in minutes for a Temporary Access Pass. Value can be any integer between the minimumLifetimeInMinutes and maximumLifetimeInMinutes. | - |
| IsUsableOnce | Write | Boolean | If true, all the passes in the tenant will be restricted to one-time use. If false, passes in the tenant can be created to be either one-time use or reusable. | - |
| MaximumLifetimeInMinutes | Write | UInt32 | Maximum lifetime in minutes for any Temporary Access Pass created in the tenant. Value can be between 10 and 43200 minutes \(equivalent to 30 days\). | - |
| MinimumLifetimeInMinutes | Write | UInt32 | Minimum lifetime in minutes for any Temporary Access Pass created in the tenant. Value can be between 10 and 43200 minutes \(equivalent to 30 days\). | - |
| ExcludeTargets | Write | AuthenticationMethodPolicyTemporaryExcludeTarget\[\] | Displayname of the groups of users that are excluded from a policy. | - |
| IncludeTargets | Write | AuthenticationMethodPolicyTemporaryIncludeTarget\[\] | Displayname of the groups of users that are included from a policy. | - |
| State | Write | String | The state of the policy. Possible values are: enabled, disabled. | `enabled`, `disabled` |
| Id | Key | String | The unique identifier for an entity. Read-only. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### AuthenticationMethodPolicyTemporaryExcludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

#### AuthenticationMethodPolicyTemporaryIncludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.AuthenticationMethod, Group.Read.All |
| Update | Policy.ReadWrite.AuthenticationMethod, Group.Read.All |

## authenticationMethodPolicyVoice resource type

### Description

Microsoft Entra Authentication Method Policy Voice

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsOfficePhoneAllowed | Write | Boolean | true if users can register office phones, otherwise, false. | - |
| ExcludeTargets | Write | AuthenticationMethodPolicyVoiceExcludeTarget\[\] | Displayname of the groups of users that are excluded from a policy. | - |
| IncludeTargets | Write | AuthenticationMethodPolicyVoiceIncludeTarget\[\] | Displayname of the groups of users that are included from a policy. | - |
| State | Write | String | The state of the policy. Possible values are: enabled, disabled. | `enabled`, `disabled` |
| Id | Key | String | The unique identifier for an entity. Read-only. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### AuthenticationMethodPolicyVoiceExcludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

#### AuthenticationMethodPolicyVoiceIncludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `user`, `group`, `unknownFutureValue` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.AuthenticationMethod, Group.Read.All |
| Update | Policy.ReadWrite.AuthenticationMethod, Group.Read.All |

## authenticationMethodPolicyX509 resource type

### Description

Microsoft Entra Authentication Method Policy X509

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AuthenticationModeConfiguration | Write | MSFT\_MicrosoftGraphx509CertificateAuthenticationModeConfiguration | Defines strong authentication configurations. This configuration includes the default authentication mode and the different rules for strong authentication bindings. | - |
| CertificateUserBindings | Write | MSFT\_MicrosoftGraphx509CertificateUserBinding\[\] | Defines fields in the X.509 certificate that map to attributes of the Microsoft Entra user object in order to bind the certificate to the user. The priority of the object determines the order in which the binding is carried out. The first binding that matches will be used and the rest ignored. | - |
| ExcludeTargets | Write | AuthenticationMethodPolicyX509ExcludeTarget\[\] | Displayname of the groups of users that are excluded from a policy. | - |
| IncludeTargets | Write | AuthenticationMethodPolicyX509IncludeTarget\[\] | Displayname of the groups of users that are included from a policy. | - |
| State | Write | String | The state of the policy. Possible values are: enabled, disabled. | `enabled`, `disabled` |
| Id | Key | String | The unique identifier for an entity. Read-only. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_MicrosoftGraphX509CertificateAuthenticationModeConfiguration

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Rules | Write | MSFT\_MicrosoftGraphX509CertificateRule\[\] | Rules are configured in addition to the authentication mode to bind a specific x509CertificateRuleType to an x509CertificateAuthenticationMode. For example, bind the policyOID with identifier 1.32.132.343 to x509CertificateMultiFactor authentication mode. | - |
| X509CertificateAuthenticationDefaultMode | Write | String | The type of strong authentication mode. The possible values are: x509CertificateSingleFactor, x509CertificateMultiFactor, unknownFutureValue. | `x509CertificateSingleFactor`, `x509CertificateMultiFactor`, `unknownFutureValue` |

#### MSFT\_MicrosoftGraphX509CertificateRule

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Identifier | Write | String | The identifier of the X.509 certificate. Required. | - |
| X509CertificateAuthenticationMode | Write | String | The type of strong authentication mode. The possible values are: x509CertificateSingleFactor, x509CertificateMultiFactor, unknownFutureValue. Required. | `x509CertificateSingleFactor`, `x509CertificateMultiFactor`, `unknownFutureValue` |
| X509CertificateRuleType | Write | String | The type of the X.509 certificate mode configuration rule. The possible values are: issuerSubject, policyOID, unknownFutureValue. Required. | `issuerSubject`, `policyOID`, `unknownFutureValue` |

#### MSFT\_MicrosoftGraphX509CertificateUserBinding

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Priority | Write | UInt32 | The priority of the binding. Microsoft Entra uses the binding with the highest priority. This value must be a non-negative integer and unique in the collection of objects in the certificateUserBindings property of an x509CertificateAuthenticationMethodConfiguration object. Required | - |
| UserProperty | Write | String | Defines the Microsoft Entra user property of the user object to use for the binding. The possible values are: userPrincipalName, onPremisesUserPrincipalName, email. Required. | - |
| X509CertificateField | Write | String | The field on the X.509 certificate to use for the binding. The possible values are: PrincipalName, RFC822Name. | - |

#### AuthenticationMethodPolicyX509ExcludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `group`, `unknownFutureValue` |

#### AuthenticationMethodPolicyX509IncludeTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The object identifier of an Microsoft Entra group. | - |
| isRegistrationRequired | Write | Boolean | Determines if the user is enforced to register the authentication method. | - |
| TargetType | Write | String | The type of the authentication method target. Possible values are: group and unknownFutureValue. | `group`, `unknownFutureValue` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.AuthenticationMethod, Group.Read.All |
| Update | Policy.ReadWrite.AuthenticationMethod, Group.Read.All |

## authenticationStrengthPolicy resource type

### Description

Microsoft Entra Authentication Strength Policy

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | The name of the policy. | - |
| Description | Write | String | A description of the policy. | - |
| Id | Write | String | The unique identifier of the policy. | - |
| AllowedCombinations | Write | StringArray\[\] | The authentication method combinations allowed by this authentication strength policy. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Security Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.AuthenticationMethod |
| Update | Policy.ReadWrite.AuthenticationMethod |

## authorizationPolicy resource type

### Description

This resource configures the Microsoft Entra Authorization Policy.

The policy is managed using the BETA API. Some properties are added in the API but not in the resource

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes.' | `Yes` |
| DisplayName | Write | String | Display name for this policy. | - |
| Description | Write | String | Description of this policy. | - |
| AllowedToSignUpEmailBasedSubscriptions | Write | Boolean | Boolean Indicates whether users can sign up for email based subscriptions. | - |
| AllowedToUseSSPR | Write | Boolean | Boolean Indicates whether the Self-Serve Password Reset feature can be used by users on the tenant. | - |
| AllowEmailVerifiedUsersToJoinOrganization | Write | Boolean | Boolean Indicates whether a user can join the tenant by email validation. | - |
| AllowInvitesFrom | Write | String | Indicates who can invite external users to the organization. Possible values are: None, AdminsAndGuestInviters, AdminsGuestInvitersAndAllMembers, Everyone. Everyone is the default setting for all cloud environments except US Government. | `None`, `AdminsAndGuestInviters`, `AdminsGuestInvitersAndAllMembers`, `Everyone` |
| BlockMsolPowershell | Write | Boolean | Boolean To disable the use of MSOL PowerShell, set this property to true. This disables user-based access to the legacy service endpoint used by MSOL PowerShell. This doesn't affect Microsoft Entra Connect or Microsoft Graph. | - |
| DefaultUserRoleAllowedToCreateApps | Write | Boolean | Boolean Indicates whether the default user role can create applications. | - |
| DefaultUserRoleAllowedToCreateSecurityGroups | Write | Boolean | Boolean Indicates whether the default user role can create security groups. | - |
| DefaultUserRoleAllowedToReadBitlockerKeysForOwnedDevice | Write | Boolean | Indicates whether the registered owners of a device can read their own BitLocker recovery keys with default user role. | - |
| DefaultUserRoleAllowedToCreateTenants | Write | Boolean | Indicates whether the default user role can create tenants. This setting corresponds to the Restrict nonadmin users from creating tenants setting in the User settings menu in the Azure portal. When this setting is false, users assigned the Tenant Creator role can still create tenants. | - |
| DefaultUserRoleAllowedToReadOtherUsers | Write | Boolean | Boolean Indicates whether the default user role can read other users. | - |
| GuestUserRole | Write | String | The role that should be granted to guest users. Refer to List unifiedRoleDefinitions to find the list of available role templates. Only supported roles today are User, Guest User, and Restricted Guest User \(2af84b1e-32c8-42b7-82bc-daa82404023b\). | `Guest`, `RestrictedGuest`, `User` |
| PermissionGrantPolicyIdsAssignedToDefaultUserRole | Write | StringArray\[\] | String collection Indicates if user consent to apps is allowed, and if it's, which permission to grant consent and which app consent policy \(permissionGrantPolicy\) govern the permission for users to grant consent. Value should be in the format managePermissionGrantsForSelf.{id}, where {id} is the id of a built-in or custom app consent policy. An empty list indicates user consent to apps is disabled. | - |
| Ensure | Write | String | Specify that the Azure Authorization Policy should exist. | `Present` |

### Microsoft Entra Permissions

To authenticate via Microsoft Graph, this resource required the following Application permissions:

- **Automate**

  - Policy.Read.All
  - Policy.ReadWrite.Authorization

- **Export**

  - Policy.Read.All

NOTE: All permissions listed require admin consent.

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Privileged Role Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.All |
| Update | Policy.ReadWrite.Authorization |

## conditionalAccessPolicy resource type

### Description

This resource configures a Microsoft Entra conditional access policy.

### Parameters

\| Parameter \| Attribute \| DataType \| Description \| Allowed Values \| \| --- \| --- \| --- \| --- \| --- \| \| DisplayName \| Key \| String \| The display name of the conditional access policy. \| - \| \| Id \| Write \| String \| Specifies the GUID for the Policy. \| - \| \| State \| Write \| String \| Specifies the State of the Policy. \| `disabled`, `enabled`, `enabledForReportingButNotEnforced` \| \| IncludeApplications \| Write \| StringArray\[\] \| The cloud apps included in the scope of the policy. \| - \| \| ApplicationsFilter \| Write \| String \| A rule with syntax similar to membership rules for groups in Microsoft Entra ID. \| - \| \| ApplicationsFilterMode \| Write \| String \| The mode to use for the filter. Possible values are `include` or `exclude`. \| `include`, `exclude` \| \| ExcludeApplications \| Write \| StringArray\[\] \| The cloud apps excluded from the scope of the policy. \| - \| \| IncludeUserActions \| Write \| StringArray\[\] \| The user actions included in the scope of the policy. \| - \| \| IncludeUsers \| Write \| StringArray\[\] \| The users included in the scope of the policy. \| - \| \| ExcludeUsers \| Write \| StringArray\[\] \| The users excluded from the scope of the policy. \| - \| \| IncludeGroups \| Write \| StringArray\[\] \| The groups included in the scope of the policy. \| - \| \| ExcludeGroups \| Write \| StringArray\[\] \| The groups excluded from the scope of the policy. \| - \| \| IncludeRoles \| Write \| StringArray\[\] \| The Microsoft Entra admin roles included in the scope of the policy. \| - \| \| ExcludeRoles \| Write \| StringArray\[\] \| The Microsoft Entra admin roles excluded from the scope of the policy. \| - \| \| IncludeGuestOrExternalUserTypes \| Write \| StringArray\[\] \| The included internal guests or external user types. A multi-valued property. Supported values are: `b2bCollaborationGuest`, `b2bCollaborationMember`, `b2bDirectConnectUser`, `internalGuest`, `otherExternalUser`, `serviceProvider`, and `unknownFutureValue`. \| `none`, `internalGuest`, `b2bCollaborationGuest`, `b2bCollaborationMember`, `b2bDirectConnectUser`, `otherExternalUser`, `serviceProvider`, `unknownFutureValue` \| \| IncludeExternalTenantsMembershipKind \| Write \| String \| The included tenants membership kind. The possible values are: `all`, `enumerated`, `unknownFutureValue`. The value `enumerated` references an object of **conditionalAccessEnumeratedExternalTenants** derived type. \| ``, `all`, `enumerated`, `unknownFutureValue` | | IncludeExternalTenantsMembers | Write | StringArray[] | The collection of tenant IDs included in the scope of the conditional access policy for guests and external users. | - | | ExcludeGuestOrExternalUserTypes | Write | StringArray[] | The excluded internal guests or external user types. A multi-valued property. Supported values are: `b2bCollaborationGuest`, `b2bCollaborationMember`, `b2bDirectConnectUser`, `internalGuest`, `otherExternalUser`, `serviceProvider`, and `unknownFutureValue`. | `none`, `internalGuest`, `b2bCollaborationGuest`, `b2bCollaborationMember`, `b2bDirectConnectUser`, `otherExternalUser`, `serviceProvider`, `unknownFutureValue` | | ExcludeExternalTenantsMembershipKind | Write | String | The excluded tenants membership kind. The possible values are: `all`, `enumerated`, `unknownFutureValue`. The value `enumerated` references an object of **conditionalAccessEnumeratedExternalTenants** derived type. | ``, `all`, `enumerated`, `unknownFutureValue` \| \| ExcludeExternalTenantsMembers \| Write \| StringArray\[\] \| The collection of tenant IDs excluded from the scope of the conditional access policy for guests and external users. \| - \| \| IncludePlatforms \| Write \| StringArray\[\] \| The client device platforms included in the scope of the policy. \| - \| \| ExcludePlatforms \| Write \| StringArray\[\] \| The client device platforms excluded from the scope of the policy. \| - \| \| IncludeLocations \| Write \| StringArray\[\] \| The Microsoft Entra named locations included in the scope of the policy. \| - \| \| ExcludeLocations \| Write \| StringArray\[\] \| The Microsoft Entra named locations excluded from the scope of the policy. \| - \| \| DeviceFilterMode \| Write \| String \| The client device filter mode of the policy. \| `include`, `exclude` \| \| DeviceFilterRule \| Write \| String \| The client device filter rule of the policy. \| - \| \| UserRiskLevels \| Write \| StringArray\[\] \| The Microsoft Entra ID Protection user risk levels in scope of the policy. \| - \| \| SignInRiskLevels \| Write \| StringArray\[\] \| The Microsoft Entra ID Protection sign-in risk levels in scope of the policy. \| - \| \| ClientAppTypes \| Write \| StringArray\[\] \| The client app types in scope of the policy. \| - \| \| GrantControlOperator \| Write \| String \| The operator to use for grant controls. \| `AND`, `OR` \| \| BuiltInControls \| Write \| StringArray\[\] \| The list of built-in grant controls to be applied by the policy. \| - \| \| ApplicationEnforcedRestrictionsIsEnabled \| Write \| Boolean \| Specifies whether application enforced restrictions are enabled in the policy. \| - \| \| CloudAppSecurityIsEnabled \| Write \| Boolean \| Specifies whether Cloud App Security is enforced by the policy. \| - \| \| CloudAppSecurityType \| Write \| String \| Specifies the Cloud App Security control enforced by the policy. \| - \| \| SignInFrequencyValue \| Write \| UInt32 \| The sign-in frequency time in the specified unit enforced by the policy. \| - \| \| TermsOfUse \| Write \| String \| The display name of the terms of use to assign. \| - \| \| CustomAuthenticationFactors \| Write \| StringArray\[\] \| The custom controls assigned to the grant property of this policy. \| - \| \| SignInFrequencyType \| Write \| String \| The sign-in frequency unit \(days or hours\) used by the policy. \| `Days`, `Hours`, ``| | SignInFrequencyIsEnabled | Write | Boolean | Specifies whether sign-in frequency is enforced by the policy. | - | | SignInFrequencyInterval | Write | String | The sign-in frequency interval. Possible values are: `timeBased`, `everyTime`, and `unknownFutureValue`. | `timeBased`, `everyTime`, `unknownFutureValue` | | PersistentBrowserIsEnabled | Write | Boolean | Specifies whether browser persistence is controlled by the policy. | - | | PersistentBrowserMode | Write | String | Specifies the browser persistence control enforced by the policy. | `Always`, `Never`,`` \| \| AuthenticationStrength \| Write \| String \| The name of the associated authentication strength policy. \| - \| \| TransferMethods \| Write \| String \| The names of the associated authentication flow transfer methods. Possible values are: `deviceCodeFlow`, `authenticationTransfer`, or `deviceCodeFlow, authenticationTransfer`. \| - \| \| AuthenticationContexts \| Write \| StringArray\[\] \| The authentication context class references. \| - \| \| Ensure \| Write \| String \| Specifies whether the conditional access policy should exist or not. \| `Present`, `Absent` \|

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Conditional Access Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Agreement.Read.All, Application.Read.All, Group.Read.All, Policy.Read.All, RoleManagement.Read.Directory, User.Read.All, CustomSecAttributeDefinition.Read.All |
| Update | Agreement.Read.All, Application.Read.All, Group.Read.All, Policy.Read.All, Policy.ReadWrite.ConditionalAccess, RoleManagement.Read.Directory, User.Read.All, CustomSecAttributeDefinition.Read.All |

## crossTenantAccessPolicy resource type

### Description

This resource manages Microsoft Entra Cross Tenant Access Policies.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes'. | `Yes` |
| DisplayName | Write | String | The name of the policy. | - |
| AllowedCloudEndpoints | Write | StringArray\[\] | Used to specify which Microsoft clouds an organization would like to collaborate with. By default, this value is empty. | `microsoftonline.com`, `microsoftonline.us`, `partner.microsoftonline.cn` |
| Ensure | Write | String | Specify if the policy should exist or not. | `Present` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Security Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.All |
| Update | Policy.ReadWrite.CrossTenantAccess |

## crossTenantAccessPolicyConfigurationDefault resource type

### Description

This resource manages Microsoft Entra Cross Tenant Access Policies Configuration Default.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes'. | `Yes` |
| B2BCollaborationInbound | Write | CrossTenantAccessPolicyB2BSetting | Defines your partner-specific configuration for users from other organizations accessing your resources via Microsoft Entra B2B collaboration. | - |
| B2BCollaborationOutbound | Write | CrossTenantAccessPolicyB2BSetting | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B collaboration. | - |
| B2BDirectConnectInbound | Write | CrossTenantAccessPolicyB2BSetting | Defines your partner-specific configuration for users from other organizations accessing your resources via Microsoft Entra B2B direct connect. | - |
| B2BDirectConnectOutbound | Write | CrossTenantAccessPolicyB2BSetting | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B direct connect. | - |
| InboundTrust | Write | CrossTenantAccessPolicyInboundTrust | Determines the partner-specific configuration for trusting other Conditional Access claims from external Microsoft Entra organizations. | - |
| Ensure | Write | String | Specify if the instance should exist or not. | `Present` |

#### CrossTenantAccessPolicyTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Target | Write | String | The unique identifier of the user, group, or application; one of the following keywords: AllUsers and AllApplications; or for targets that are applications, you may use reserved values. | - |
| TargetType | Write | String | The type of resource that you want to target. The possible values are: user, group, application, unknownFutureValue. | `user`, `group`, `application`, `unknownFutureValue` |

#### CrossTenantAccessPolicyTargetConfiguration

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AccessType | Write | String | Defines whether access is allowed or blocked. The possible values are: allowed, blocked, unknownFutureValue. | `allowed`, `blocked`, `unknownFutureValue` |
| Targets | Write | CrossTenantAccessPolicyTarget\[\] | Specifies whether to target users, groups, or applications with this rule. | - |

#### CrossTenantAccessPolicyB2BSetting

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Applications | Write | CrossTenantAccessPolicyTargetConfiguration | The list of applications targeted with your cross-tenant access policy. | - |
| UsersAndGroups | Write | CrossTenantAccessPolicyTargetConfiguration | The list of users and groups targeted with your cross-tenant access policy. | - |

#### CrossTenantAccessPolicyInboundTrust

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsCompliantDeviceAccepted | Write | Boolean | Specifies whether compliant devices from external Microsoft Entra organizations are trusted. | - |
| IsHybridAzureADJoinedDeviceAccepted | Write | Boolean | Specifies whether hybrid Microsoft Entra joined devices from external Microsoft Entra organizations are trusted. | - |
| IsMfaAccepted | Write | Boolean | Specifies whether MFA from external Microsoft Entra organizations is trusted. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Security Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.All |
| Update | Policy.ReadWrite.CrossTenantAccess |

## crossTenantAccessPolicyConfigurationPartner resource type

### Description

This resource manages Microsoft Entra Cross Tenant Access Policies Configuration Partner.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| PartnerTenantId | Key | String | The tenant identifier for the partner Azure Active Directory \(Microsoft Entra\) organization. | - |
| B2BCollaborationInbound | Write | CrossTenantAccessPolicyB2BSetting | Defines your partner-specific configuration for users from other organizations accessing your resources via Microsoft Entra B2B collaboration. | - |
| B2BCollaborationOutbound | Write | CrossTenantAccessPolicyB2BSetting | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B collaboration. | - |
| B2BDirectConnectInbound | Write | CrossTenantAccessPolicyB2BSetting | Defines your partner-specific configuration for users from other organizations accessing your resources via Microsoft Entra B2B direct connect. | - |
| B2BDirectConnectOutbound | Write | CrossTenantAccessPolicyB2BSetting | Defines your partner-specific configuration for users in your organization going outbound to access resources in another organization via Microsoft Entra B2B direct connect. | - |
| AutomaticUserConsentSettings | Write | CrossTenantAccessPolicyAutomaticUserConsentSettings | Determines the partner-specific configuration for accepting trust claims from other tenant invitations. | - |
| InboundTrust | Write | CrossTenantAccessPolicyInboundTrust | Determines the partner-specific configuration for trusting other Conditional Access claims from external Microsoft Entra organizations. | - |
| Ensure | Write | String | Specify if the policy should exist or not. | `Present`, `Absent` |

#### CrossTenantAccessPolicyTarget

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Target | Write | String | The unique identifier of the user, group, or application; one of the following keywords: AllUsers and AllApplications; or for targets that are applications, you may use reserved values. | - |
| TargetType | Write | String | The type of resource that you want to target. The possible values are: user, group, application, unknownFutureValue. | `user`, `group`, `application`, `unknownFutureValue` |

#### CrossTenantAccessPolicyTargetConfiguration

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AccessType | Write | String | Defines whether access is allowed or blocked. The possible values are: allowed, blocked, unknownFutureValue. | `allowed`, `blocked`, `unknownFutureValue` |
| Targets | Write | CrossTenantAccessPolicyTarget\[\] | Specifies whether to target users, groups, or applications with this rule. | - |

#### CrossTenantAccessPolicyB2BSetting

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Applications | Write | CrossTenantAccessPolicyTargetConfiguration | The list of applications targeted with your cross-tenant access policy. | - |
| UsersAndGroups | Write | CrossTenantAccessPolicyTargetConfiguration | The list of users and groups targeted with your cross-tenant access policy. | - |

#### CrossTenantAccessPolicyAutomaticUserConsentSettings

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| InboundAllowed | Write | Boolean | Specifies whether you want to automatically trust Inbound invitations. | - |
| OutboundAllowed | Write | Boolean | Specifies whether you want to automatically trust Outbound invitations. | - |

#### CrossTenantAccessPolicyInboundTrust

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsCompliantDeviceAccepted | Write | Boolean | Specifies whether compliant devices from external Microsoft Entra organizations are trusted. | - |
| IsHybridAzureADJoinedDeviceAccepted | Write | Boolean | Specifies whether hybrid Microsoft Entra joined devices from external Microsoft Entra organizations are trusted. | - |
| IsMfaAccepted | Write | Boolean | Specifies whether MFA from external Microsoft Entra organizations is trusted. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Global Reader |
| Update | Security Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.All |
| Update | Policy.ReadWrite.CrossTenantAccess |

## entitlementManagementAccessPackage resource type

### Description

This resource configures a Microsoft Entra ID Governance entitlement management access package.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | The display name of the access package. | - |
| Id | Write | String | The Id of the access package. | - |
| CatalogId | Write | String | Identifier of the access package catalog referencing this access package. | - |
| Description | Write | String | The description of the access package. | - |
| IsHidden | Write | Boolean | Whether the access package is hidden from the requestor. | - |
| IsRoleScopesVisible | Write | Boolean | Indicates whether role scopes are visible. | - |
| AccessPackageResourceRoleScopes | Write | MSFT\_AccessPackageResourceRoleScope\[\] | The resources and roles included in the access package. | - |
| IncompatibleAccessPackages | Write | StringArray\[\] | The access packages whose assigned users are ineligible to be assigned this access package. | - |
| AccessPackagesIncompatibleWith | Write | StringArray\[\] | The access packages that are incompatible with this package. | - |
| IncompatibleGroups | Write | StringArray\[\] | The groups whose members are ineligible to be assigned this access package. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures the policy is removed. | `Present`, `Absent` |

#### MSFT\_AccessPackageResourceRoleScope

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Id | Write | String | The unique identifier of the resource role scope. | - |
| AccessPackageResourceOriginId | Write | String | The origin identifier of the resource. | - |
| AccessPackageResourceRoleDisplayName | Write | String | The display name of the resource role. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Identity Governance Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | EntitlementManagement.Read.All |
| Update | EntitlementManagement.ReadWrite.All |

## entitlementManagementAccessPackageAssignmentPolicy resource type

### Description

This resource configures an Microsoft Entra Entitlement Management Access Package Assignment Policy.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | The display name of the policy. | - |
| Id | Write | String | Id of the access package assignment policy. | - |
| AccessPackageId | Write | String | Identifier of the access package. | - |
| AccessReviewSettings | Write | MSFT\_MicrosoftGraphassignmentreviewsettings | Who must review, and how often, the assignments to the access package from this policy. This property is null if reviews aren't required. | - |
| CanExtend | Write | Boolean | Indicates whether a user can extend the access package assignment duration after approval. | - |
| Description | Write | String | The description of the policy. | - |
| DurationInDays | Write | UInt32 | The number of days in which assignments from this policy last until they're expired. | - |
| ExpirationDateTime | Write | String | The expiration date for assignments created in this policy. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z | - |
| Questions | Write | MSFT\_MicrosoftGraphaccesspackagequestion\[\] | Questions that are posed to the requestor. | - |
| RequestApprovalSettings | Write | MSFT\_MicrosoftGraphapprovalsettings | Who must approve requests for access package in this policy. | - |
| RequestorSettings | Write | MSFT\_MicrosoftGraphrequestorsettings | Who can request this access package from this policy. | - |
| CustomExtensionHandlers | Write | MSFT\_MicrosoftGraphcustomextensionhandler\[\] | The collection of stages when to execute one or more custom access package workflow extensions. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### MSFT\_MicrosoftGraphassignmentreviewsettings

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AccessReviewTimeoutBehavior | Write | String | The default decision to apply if the request isn't reviewed within the period specified in durationInDays. | `acceptAccessRecommendation`, `keepAccess`, `removeAccess`, `unknownFutureValue` |
| DurationInDays | Write | UInt32 | The number of days within which reviewers should provide input. | - |
| IsAccessRecommendationEnabled | Write | Boolean | Specifies whether to display recommendations to the reviewer. The default value is true | - |
| IsApprovalJustificationRequired | Write | Boolean | Specifies whether the reviewer must provide justification for the approval. The default value is true. | - |
| IsEnabled | Write | Boolean | If true, access reviews are required for assignments from this policy. | - |
| RecurrenceType | Write | String | The interval for recurrence, such as monthly or quarterly. | - |
| ReviewerType | Write | String | Who should be asked to do the review, either Self or Reviewers. | - |
| Reviewers | Write | MSFT\_MicrosoftGraphuserset\[\] | If the reviewerType is Reviewers, this collection specifies the users who are reviewers, either by ID or as members of a group, using a collection of singleUser and groupMembers. | - |
| StartDateTime | Write | String | When the first review should start. | - |

#### MSFT\_MicrosoftGraphuserset

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | The type of the resource | `#microsoft.graph.singleUser`, `#microsoft.graph.groupMembers`, `#microsoft.graph.requestorManager`, `#microsoft.graph.internalSponsors`, `#microsoft.graph.externalSponsors`, `#microsoft.graph.connectedOrganizationMembers` |
| Id | Write | String | The id of the resource. | - |
| IsBackup | Write | Boolean | Indicates whether the resource is a backup fallback approver. | - |
| ManagerLevel | Write | UInt32 | The hierarchical level of the manager with respect to the requestor. For example, the direct manager of a requestor would have a managerLevel of 1, while the manager of the requestor's manager would have a managerLevel of 2. Default value for managerLevel is 1. Possible values for this property range from 1 to 2. | - |

#### MSFT\_MicrosoftGraphaccesspackagequestion

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | The type of the resource | `#microsoft.graph.accessPackageMultipleChoiceQuestion`, `#microsoft.graph.accessPackageTextInputQuestion` |
| Id | Write | String | ID of the question. | - |
| IsAnswerEditable | Write | Boolean | Specifies whether the requestor is allowed to edit answers to questions. | - |
| IsRequired | Write | Boolean | Whether the requestor is required to supply an answer or not. | - |
| Sequence | Write | UInt32 | Relative position of this question when displaying a list of questions to the requestor. | - |
| QuestionText | Write | MSFT\_MicrosoftGraphaccessPackageLocalizedContent | The text of the question to show to the requestor. | - |
| Choices | Write | MSFT\_MicrosoftGraphaccessPackageAnswerChoice\[\] | List of answer choices. | - |
| AllowsMultipleSelection | Write | Boolean | Indicates whether requestor can select multiple choices as their answer. | - |
| RegexPattern | Write | String | This is the regex pattern that the corresponding text answer must follow. | - |
| IsSingleLineQuestion | Write | Boolean | Indicates whether the answer is in single or multiple line format. | - |

#### MSFT\_MicrosoftGraphaccessPackageLocalizedContent

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DefaultText | Write | String | The fallback string, which is used when a requested localization isn't available. Required. | - |
| LocalizedTexts | Write | MSFT\_MicrosoftGraphaccessPackageLocalizedText\[\] | Content represented in a format for a specific locale. | - |

#### MSFT\_MicrosoftGraphaccessPackageLocalizedText

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Text | Write | String | The text in the specific language. Required. | - |
| LanguageCode | Write | String | The ISO code for the intended language. Required. | - |

#### MSFT\_MicrosoftGraphaccessPackageAnswerChoice

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ActualValue | Write | String | The actual value of the selected choice. This is typically a string value that is understandable by applications. Required. | - |
| displayValue | Write | MSFT\_MicrosoftGraphaccessPackageLocalizedContent | The localized display values shown to the requestor and approvers. Required. | - |

#### MSFT\_MicrosoftGraphapprovalsettings

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ApprovalMode | Write | String | One of SingleStage, Serial, Parallel, NoApproval \(default\). NoApproval is used when isApprovalRequired is false. | `SingleStage`, `Serial`, `Parallel`, `NoApproval` |
| ApprovalStages | Write | MSFT\_MicrosoftGraphapprovalstage1\[\] | If approval is required, the one or two elements of this collection define each of the stages of approval. An empty array if no approval is required. | - |
| IsApprovalRequired | Write | Boolean | Indicates whether approval is required for requests in this policy. | - |
| IsApprovalRequiredForExtension | Write | Boolean | Indicates whether approval is required for a user to extend their assignment. | - |
| IsRequestorJustificationRequired | Write | Boolean | Indicates whether the requestor is required to supply a justification in their request. | - |

#### MSFT\_MicrosoftGraphapprovalstage1

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ApprovalStageTimeOutInDays | Write | UInt32 | The number of days that a request can be pending a response before it's automatically denied. | - |
| EscalationTimeInMinutes | Write | UInt32 | Indicates whether the approver is required to provide a justification for approving a request. | - |
| IsApproverJustificationRequired | Write | Boolean | If true, then one or more escalation approvers are configured in this approval stage. | - |
| IsEscalationEnabled | Write | Boolean | If escalation is required, the time a request can be pending a response from a primary approver. | - |
| PrimaryApprovers | Write | MSFT\_MicrosoftGraphuserset\[\] | The users who are asked to approve requests. A collection of singleUser, groupMembers, requestorManager, internalSponsors and externalSponsors. When creating or updating a policy, include at least one userSet in this collection. | - |
| EscalationApprovers | Write | MSFT\_MicrosoftGraphuserset\[\] | If escalation is enabled and the primary approvers do not respond before the escalation time, the escalationApprovers are the users who are asked to approve requests. This can be a collection of singleUser, groupMembers, requestorManager, internalSponsors and externalSponsors. When creating or updating a policy, if there are no escalation approvers, or escalation approvers are not required for the stage, the value of this property should be an empty collection. | - |

#### MSFT\_MicrosoftGraphrequestorsettings

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AcceptRequests | Write | Boolean | Indicates whether new requests are accepted on this policy. | - |
| AllowedRequestors | Write | MSFT\_MicrosoftGraphuserset\[\] | The users who are allowed to request on this policy, which can be singleUser, groupMembers, and connectedOrganizationMembers. | - |
| ScopeType | Write | String | Who can request. | `NoSubjects`, `SpecificDirectorySubjects`, `SpecificConnectedOrganizationSubjects`, `AllConfiguredConnectedOrganizationSubjects`, `AllExistingConnectedOrganizationSubjects`, `AllExistingDirectoryMemberUsers`, `AllExistingDirectorySubjects`, `AllExternalSubjects` |

#### MSFT\_MicrosoftGraphcustomextensionhandler

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| CustomExtensionId | Write | String | Indicates which custom workflow extension is executed at this stage. | - |
| Stage | Write | String | Indicates the stage of the access package assignment request workflow when the access package custom extension runs. | `assignmentRequestCreated`, `assignmentRequestApproved`, `assignmentRequestGranted`, `assignmentRequestRemoved`, `assignmentFourteenDaysBeforeExpiration`, `assignmentOneDayBeforeExpiration`, `unknownFutureValue` |
| Id | Write | String | Identifier of the stage. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Identity Governance Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | EntitlementManagement.Read.All |
| Update | EntitlementManagement.ReadWrite.All |

## entitlementManagementAccessPackageCatalog resource type

### Description

This resource configures a Microsoft Entra ID Governance entitlement management access package catalog.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | The display name of the access package catalog. | - |
| Id | Write | String | The unique identifier of the access package catalog. | - |
| CatalogStatus | Write | String | Indicates whether the access packages are available for management. Has the value `Published` if available. | - |
| CatalogType | Write | String | The type of the catalog. Possible values are: `UserManaged` or `ServiceDefault`. | `UserManaged`, `ServiceDefault` |
| Description | Write | String | The description of the access package catalog. | - |
| IsExternallyVisible | Write | Boolean | Indicates whether the access packages in this catalog can be requested by users outside of the tenant. | - |
| Ensure | Write | String | Specifies whether the catalog should exist or not. `Present` ensures the catalog exists; `Absent` ensures the catalog is removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Identity Governance Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | EntitlementManagement.Read.All |
| Update | EntitlementManagement.ReadWrite.All |

## entitlementManagementAccessPackageCatalogResource resource type

### Description

This resource configures a Microsoft Entra ID Governance entitlement management access package catalog resource.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | The display name of the resource, such as the application name, group name, or site name. | - |
| Id | Write | String | The unique identifier of the access package catalog resource. | - |
| CatalogId | Write | String | The unique identifier of the access package catalog. | - |
| AddedBy | Write | String | The name of the user or application that first added this resource. This property is read-only. | - |
| AddedOn | Write | String | The date and time when the resource was added, in ISO 8601 format \(UTC\). For example, midnight UTC on January 1, 2014 is `2014-01-01T00:00:00Z`. This property is read-only. | - |
| Attributes | Write | MSFT\_MicrosoftGraphaccesspackageresourceattribute\[\] | The attributes to be collected from the requestor and sent to the resource application. | - |
| Description | Write | String | The description of the resource. | - |
| IsPendingOnboarding | Write | Boolean | Indicates whether the resource isn't yet available for assignment. This property is read-only. | - |
| OriginId | Write | String | The unique identifier of the resource in the origin system. For a Microsoft Entra group, this is the identifier of the group. | - |
| OriginSystem | Write | String | The type of the resource in the origin system. | - |
| ResourceType | Write | String | The type of the resource. | - |
| Url | Write | String | A unique resource locator for the resource, such as the URL for signing a user into an application. | - |
| Ensure | Write | String | Specifies whether the catalog resource should exist or not. `Present` ensures the resource exists; `Absent` ensures the resource is removed. | `Present`, `Absent` |

#### MSFT\_MicrosoftGraphaccesspackageresourceattribute

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AttributeDestination | Write | MSFT\_MicrosoftGraphaccesspackageresourceattributedestination | Information about how to set the attribute. Currently uses the **accessPackageUserDirectoryAttributeStore** object type. | - |
| AttributeName | Write | String | The name of the attribute in the end system. | - |
| AttributeSource | Write | MSFT\_MicrosoftGraphaccesspackageresourceattributesource | Information about how to populate the attribute value when an **accessPackageAssignmentRequest** is being fulfilled. Currently uses the **accessPackageResourceAttributeQuestion** object type. | - |
| Id | Write | String | Id of the access package resource attribute. | - |
| IsEditable | Write | Boolean | Specifies whether or not an existing attribute value can be edited by the requester. | - |
| IsPersistedOnAssignmentRemoval | Write | Boolean | Specifies whether the attribute will remain in the end system after an assignment ends. | - |

#### MSFT\_MicrosoftGraphaccesspackageresourceattributedestination

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | Type of the access package resource attribute destination. | `#microsoft.graph.accessPackageUserDirectoryAttributeStore` |

#### MSFT\_MicrosoftGraphaccesspackageresourceattributesource

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | Type of the access package resource attribute source. | `#microsoft.graph.accessPackageResourceAttributeQuestion` |
| Question | Write | MSFT\_MicrosoftGraphaccessPackageResourceAttributeQuestion | The question asked to get the value of the attribute. | - |

#### MSFT\_MicrosoftGraphaccessPackageResourceAttributeQuestion

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | Type of the access package resource attribute question. | `#microsoft.graph.accessPackageTextInputQuestion`, `#microsoft.graph.accessPackageMultipleChoiceQuestion` |
| Id | Write | String | The unique identifier of the access package resource attribute question. | - |
| IsRequired | Write | Boolean | Indicates whether the requestor is required to supply an answer or not. | - |
| IsSingleLine | Write | Boolean | Indicates whether the answer is in single or multiple line formats. | - |
| RegexPattern | Write | String | This is the regex pattern that the corresponding text answer must follow. | - |
| Sequence | Write | UInt32 | Relative position of this question when displaying a list of questions to the requestor. | - |
| QuestionText | Write | MSFT\_MicrosoftGraphaccessPackageLocalizedContent | The text of the question to show to the requestor. | - |
| AllowsMultipleSelection | Write | Boolean | Indicates whether requestor can select multiple choices as their answer. | - |
| Choices | Write | MSFT\_MicrosoftGraphaccessPackageAnswerChoice\[\] | List of answer choices. | - |

#### MSFT\_MicrosoftGraphaccessPackageLocalizedContent

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DefaultText | Write | String | The fallback string, which is used when a requested localization isn't available. Required. | - |
| LocalizedTexts | Write | MSFT\_MicrosoftGraphaccessPackageLocalizedText\[\] | Content represented in a format for a specific locale. | - |

#### MSFT\_MicrosoftGraphaccessPackageLocalizedText

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Text | Write | String | The text in the specific language. Required. | - |
| LanguageCode | Write | String | The ISO code for the intended language. Required. | - |

#### MSFT\_MicrosoftGraphaccessPackageAnswerChoice

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ActualValue | Write | String | The actual value of the selected choice. This is typically a string value that is understandable by applications. Required. | - |
| displayValue | Write | MSFT\_MicrosoftGraphaccessPackageLocalizedContent | The localized display values shown to the requestor and approvers. Required. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Identity Governance Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | EntitlementManagement.Read.All |
| Update | EntitlementManagement.ReadWrite.All |

## entitlementManagementConnectedOrganization resource type

### Description

This resource configures an Microsoft Entra Entitlement Management Connected Organization.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | The display name of the connected organization. | - |
| Id | Write | String | The Id of the Connected organization object. | - |
| Description | Write | String | The description of the connected organization. | - |
| IdentitySources | Write | EntitlementManagementConnectedOrganizationIdentitySource\[\] | The identity sources in this connected organization. | - |
| State | Write | String | The state of a connected organization defines whether assignment policies with requestor scope type AllConfiguredConnectedOrganizationSubjects are applicable or not. | `configured`, `proposed`, `unknownFutureValue` |
| ExternalSponsors | Write | StringArray\[\] | Collection of objectID of external sponsors. the sponsor can be a user or a group. | - |
| InternalSponsors | Write | StringArray\[\] | Collection of objectID of internal sponsors. the sponsor can be a user or a group. | - |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

#### EntitlementManagementConnectedOrganizationIdentitySource

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| odataType | Write | String | Type of the identity source. | `#microsoft.graph.azureActiveDirectoryTenant`, `#microsoft.graph.crossCloudAzureActiveDirectoryTenant`, `#microsoft.graph.domainIdentitySource`, `#microsoft.graph.externalDomainFederation` |
| DisplayName | Write | String | The name of the Microsoft Entra tenant. | - |
| ExternalTenantId | Write | String | The ID of the Microsoft Entra tenant. | - |
| CloudInstance | Write | String | The ID of the cloud where the tenant is located, one of microsoftonline.com, microsoftonline.us, or partner.microsoftonline.cn. | - |
| DomainName | Write | String | The domain name. | - |
| IssuerUri | Write | String | The issuerURI of the incoming federation. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Identity Governance Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | EntitlementManagement.Read.All |
| Update | EntitlementManagement.ReadWrite.All, Directory.Read.All |

## externalIdentityPolicy resource type

### Description

Represents the tenant-wide policy that controls whether external users can leave the guest Microsoft Entra tenant by using self-service controls.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes.' | `Yes` |
| AllowDeletedIdentitiesDataRemoval | Write | Boolean | Reserved for future use. | - |
| allowExternalIdentitiesToLeave | Required | Boolean | Defines whether external users can leave the guest tenant. If set to false, self-service controls are disabled, and the admin of the guest tenant must manually remove the external user from the guest tenant. When the external user leaves the tenant, their data in the guest tenant is first soft-deleted, then permanently deleted after 30 days. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Privileged Role Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.All |
| Update | Policy.ReadWrite.ExternalIdentities |

## group resource type

### Description

This resource configures an Microsoft Entra group. IMPORTANT: It does not support mail enabled security groups or mail enabled groups that are not unified or dynamic groups.

If using with AADUser, be aware that if AADUser->MemberOf is being specified and the referenced group is configured with AADGroup->Member then a conflict may arise if the two don't match. It's usually best to choose only one of them. See AADUser

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | DisplayName of the Microsoft Entra Group | - |
| MailNickname | Key | String | Specifies a mail nickname for the group. | - |
| Description | Write | String | Specifies a description for the group. | - |
| Id | Write | String | Specifies an ID for the group. | - |
| Owners | Write | StringArray\[\] | User Service Principal values for the group's owners. | - |
| Members | Write | StringArray\[\] | User Service Principal values for the group's members. | - |
| GroupAsMembers | Write | StringArray\[\] | Displayname values for the groups member of the group. | - |
| MemberOf | Write | StringArray\[\] | DisplayName values for the groups that this group is a member of. | - |
| GroupTypes | Write | StringArray\[\] | Specifies that the group is a dynamic group. To create a dynamic group, specify a value of DynamicMembership. | - |
| MembershipRule | Write | String | Specifies the membership rule for a dynamic group. | - |
| MembershipRuleProcessingState | Write | String | Specifies the rule processing state. The acceptable values for this parameter are: On. Process the group rule or Paused. Stop processing the group rule. | `On`, `Paused` |
| SecurityEnabled | Required | Boolean | Specifies whether the group is security enabled. For security groups, this value must be $True. | - |
| MailEnabled | Required | Boolean | Specifies whether this group is mail enabled. Currently, you can't create mail enabled groups in Microsoft Entra. | - |
| IsAssignableToRole | Write | Boolean | Specifies whether this group can be assigned a role. Only available when creating a group and can't be modified after group is created. | - |
| AssignedToRole | Write | StringArray\[\] | DisplayName values for the roles that the group is assigned to. | - |
| Visibility | Write | String | This parameter determines the visibility of the group's content and members list. | `Public`, `Private`, `HiddenMembership` |
| AssignedLicenses | Write | GroupLicense\[\] | List of Licenses assigned to the group. | - |
| Ensure | Write | String | Specify if the Microsoft Entra Group should exist or not. | `Present`, `Absent` |

#### GroupLicense

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisabledPlans | Write | StringArray\[\] | A collection of the unique identifiers for plans that have been disabled. | - |
| SkuId | Write | String | The unique identifier for the SKU. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | None |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Application.Read.All, Device.Read.All, Directory.Read.All, Group.Read.All, ReportSettings.Read.All |
| Update | Application.Read.All, Device.Read.All, Directory.ReadWrite.All, Group.ReadWrite.All, Organization.Read.All, RoleManagement.ReadWrite.Directory, User.Read.All, ReportSettings.ReadWrite.All |

## groupLifecyclePolicy resource type

### Description

This resource configures an Microsoft Entra Group Lifecycle Policy \(for example, Expiration\).

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes.' | `Yes` |
| GroupLifetimeInDays | Required | UInt32 | The number of days a group can exist before it needs to be renewed. | - |
| ManagedGroupTypes | Required | String | This parameter allows the admin to select which office 365 groups the policy applies to. 'None' creates the policy in a disabled state. 'All' applies the policy to every Office 365 group in the tenant. 'Selected' allows the admin to choose specific Office 365 groups that the policy applies to. | `All`, `None`, `Selected` |
| AlternateNotificationEmails | Required | StringArray\[\] | Notification emails for groups that have no owners are sent to these email addresses. | - |
| Ensure | Write | String | Specify if the Microsoft Entra Groups Lifecycle Policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Groups Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Directory.Read.All |
| Update | Directory.ReadWrite.All |

## namedLocationPolicy resource type

### Description

This resource configures the Microsoft Entra Named Location Policies in Microsoft Entra

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| OdataType | Write | String | Specifies the Odata Type of a Named Location object in Microsoft Entra | `#microsoft.graph.countryNamedLocation`, `#microsoft.graph.ipNamedLocation`, `#microsoft.graph.compliantNetworkNamedLocation` |
| Id | Write | String | Specifies the ID of a Named Location in Microsoft Entra. | - |
| DisplayName | Key | String | Specifies the Display Name of a Named Location in Microsoft Entra | - |
| IpRanges | Write | StringArray\[\] | Specifies the IP ranges of the Named Location in Microsoft Entra | - |
| IsTrusted | Write | Boolean | Specifies the isTrusted value for the Named Location \(IP ranges only\) in Microsoft Entra | - |
| CountriesAndRegions | Write | StringArray\[\] | Specifies the countries and regions for the Named Location in Microsoft Entra | - |
| CountryLookupMethod | Write | String | Determines what method is used to decide which country/region the user is located in. Possible values are clientIpAddress\(default\) and authenticatorAppGps. | `clientIpAddress`, `authenticatorAppGps` |
| IncludeUnknownCountriesAndRegions | Write | Boolean | Specifies the includeUnknownCountriesAndRegions value for the Named Location in Microsoft Entra | - |
| Ensure | Write | String | Specify if the Microsoft Entra Named Location should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Security Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.All |
| Update | Policy.Read.All, Policy.ReadWrite.ConditionalAccess |

## roleDefinition resource type

### Description

This resource configures an Microsoft Entra role definition. To configure custom roles, you require an Microsoft Entra Premium P1 license. The account used to configure role definitions based on this resource needs either to be a "Global Administrator" or a "Privileged role administrator".

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | Specifies a display name for the role definition. | - |
| Id | Write | String | Specifies Id for the role definition. | - |
| Description | Write | String | Specifies a description for the role definition. | - |
| ResourceScopes | Write | StringArray\[\] | Specifies the resource scopes for the role definition. | - |
| IsEnabled | Required | Boolean | Specifies whether the role definition is enabled. | - |
| RolePermissions | Required | StringArray\[\] | Specifies permissions for the role definition. | - |
| TemplateId | Write | String | Specifies template id for the role definition. | - |
| Version | Write | String | Specifies version for the role definition. | - |
| Ensure | Write | String | Specify if the Microsoft Entra Role definition should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Privileged Role Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | RoleManagement.Read.Directory |
| Update | RoleManagement.ReadWrite.Directory |

## roleEligibilityScheduleRequest resource type

### Description

Represents a request for a role eligibility for a principal through PIM. The role eligibility can be permanently eligible without an expiry date or temporarily eligible with an expiry date. Inherits from request.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| Principal | Key | String | User Principal Name of the eligibility request. | - |
| RoleDefinition | Key | String | Role associated with the eligibility request. | - |
| PrincipalType | Write | String | Represented the type of principal to assign the request to. Accepted values are: Group and User. | `Group`, `User` |
| DirectoryScopeId | Write | String | Identifier of the directory object representing the scope of the role eligibility. The scope of an role eligibility determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use / for tenant-wide scope. Use appScopeId to limit the scope to an application only. Either directoryScopeId or appScopeId is required. | - |
| Id | Write | String | Identifier for the Role Eligibility Schedule Request. | - |
| AppScopeId | Write | String | Identifier of the app-specific scope when the role eligibility is scoped to an app. The scope of a role eligibility determines the set of resources for which the principal is eligible to access. App scopes are scopes that are defined and understood by this application only. Use / for tenant-wide app scopes. Use directoryScopeId to limit the scope to particular directory objects, for example, administrative units. Either directoryScopeId or appScopeId is required. | - |
| Action | Write | String | Represents the type of operation on the role eligibility request.The possible values are: adminAssign, adminUpdate, adminRemove, selfActivate, selfDeactivate, adminExtend, adminRenew, selfExtend, selfRenew, unknownFutureValue. | `adminAssign`, `adminUpdate`, `adminRemove`, `selfActivate`, `selfDeactivate`, `adminExtend`, `adminRenew`, `selfExtend`, `selfRenew`, `unknownFutureValue` |
| IsValidationOnly | Write | Boolean | Determines whether the call is a validation or an actual call. Only set this property if you want to check whether an activation is subject to additional rules like MFA before actually submitting the request. | - |
| Justification | Write | String | A message provided by users and administrators when create they create the unifiedRoleEligibilityScheduleRequest object. Optional when action is adminRemove. Whether this property is required or optional is also dependent on the settings for the Microsoft Entra role. | - |
| ScheduleInfo | Write | RoleEligibilityScheduleRequestSchedule | The period of the role eligibility. Optional when action is adminRemove. The period of eligibility is dependent on the settings of the Microsoft Entra role. | - |
| TicketInfo | Write | RoleEligibilityScheduleRequestTicketInfo | Ticket details linked to the role eligibility request including details of the ticket number and ticket system. | - |
| Ensure | Write | String | Present ensures the instance exists, absent ensures it's removed. | `Present`, `Absent` |

#### RoleEligibilityScheduleRequestScheduleRecurrenceRange

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| endDate | Required | String | The date to stop applying the recurrence pattern. Depending on the recurrence pattern of the event, the last occurrence of the meeting may not be this date. | - |
| numberOfOccurrences | Write | UInt32 | The number of times to repeat the event. Required and must be positive if type is numbered. | - |
| recurrenceTimeZone | Write | String | Time zone for the startDate and endDate properties. | - |
| startDate | Required | String | The date to start applying the recurrence pattern. The first occurrence of the meeting may be this date or later, depending on the recurrence pattern of the event. Must be the same value as the start property of the recurring event. | - |
| type | Required | String | The recurrence range. The possible values are: endDate, noEnd, numbered. | `endDate`, `noEnd`, `numbered` |

#### RoleEligibilityScheduleRequestScheduleRecurrencePattern

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| dayOfMonth | Write | UInt32 | The day of the month on which the event occurs. | - |
| daysOfWeek | Write | StringArray\[\] | A collection of the days of the week on which the event occurs. The possible values are: sunday, monday, tuesday, wednesday, thursday, friday, saturday | `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday` |
| firstDayOfWeek | Write | String | The first day of the week. | `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday` |
| index | Write | String | Specifies on which instance of the allowed days specified in daysOfWeek the event occurs, counted from the first instance in the month. The possible values are: first, second, third, fourth, last. | `first`, `second`, `third`, `fourth`, `last` |
| interval | Write | UInt32 | The number of units between occurrences, where units can be in days, weeks, months, or years, depending on the type. | - |
| month | Write | UInt32 | The month in which the event occurs. This is a number from 1 to 12. | - |
| type | Write | String | The recurrence pattern type: daily, weekly, absoluteMonthly, relativeMonthly, absoluteYearly, relativeYearly. | `daily`, `weekly`, `absoluteMonthly`, `relativeMonthly`, `absoluteYearly`, `relativeYearly` |

#### RoleEligibilityScheduleRequestScheduleRecurrence

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| pattern | Write | RoleEligibilityScheduleRequestScheduleRecurrencePattern | The frequency of an event. | - |
| range | Write | RoleEligibilityScheduleRequestScheduleRecurrenceRange | The duration of an event. | - |

#### RoleEligibilityScheduleRequestScheduleExpiration

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| duration | Write | String | The requestor's desired duration of access represented in ISO 8601 format for durations. For example, PT3H refers to three hours. If specified in a request, endDateTime should not be present and the type property should be set to afterDuration. | - |
| endDateTime | Write | String | Timestamp of date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is 2014-01-01T00:00:00Z. | - |
| type | Write | String | The requestor's desired expiration pattern type. The possible values are: notSpecified, noExpiration, afterDateTime, afterDuration. | `notSpecified`, `noExpiration`, `afterDateTime`, `afterDuration` |

#### RoleEligibilityScheduleRequestSchedule

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| expiration | Write | RoleEligibilityScheduleRequestScheduleExpiration | When the eligible or active assignment expires. | - |
| recurrence | Write | RoleEligibilityScheduleRequestScheduleRecurrence | The frequency of the eligible or active assignment. This property is currently unsupported in PIM. | - |
| startDateTime | Write | String | When the eligible or active assignment becomes active. | - |

#### RoleEligibilityScheduleRequestTicketInfo

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ticketNumber | Write | String | The ticket number. | - |
| ticketSystem | Write | String | The description of the ticket system. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Privileged Role Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | RoleEligibilitySchedule.Read.Directory, Directory.Read.All |
| Update | RoleEligibilitySchedule.ReadWrite.Directory, Directory.Read.All |

## roleSetting resource type

### Description

This resource configure existing Azure roles. All UI parameters can be configured using this resource like:

- Notifications
- require approval / ticket / justification / MFA

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | RuleDefinition DisplayName | - |
| Id | Write | String | Specifies the RoleId. | - |
| ActivationMaxDuration | Write | String | Activation maximum duration \(hours\). | - |
| ActivationReqJustification | Write | Boolean | Require justification on activation \(True/False\) | - |
| ActivationReqTicket | Write | Boolean | Require ticket information on activation \(True/False\) | - |
| ActivationReqMFA | Write | Boolean | Require MFA on activation \(True/False\) | - |
| ApprovaltoActivate | Write | Boolean | Require approval to activate \(True/False\) | - |
| ActivateApprover | Write | StringArray\[\] | Approver User UPN and/or Group Displayname | - |
| PermanentEligibleAssignmentisExpirationRequired | Write | Boolean | Allow permanent eligible assignment \(True/False\) | - |
| ExpireEligibleAssignment | Write | String | Expire eligible assignments after \(Days\) | - |
| PermanentActiveAssignmentisExpirationRequired | Write | Boolean | Allow permanent active assignment \(True/False\) | - |
| ExpireActiveAssignment | Write | String | Expire active assignments after \(Days\) | - |
| AssignmentReqMFA | Write | Boolean | Require Azure Multi-Factor Authentication on active assignment \(True/False\) | - |
| AssignmentReqJustification | Write | Boolean | Require justification on active assignment \(True/False\) | - |
| ElegibilityAssignmentReqMFA | Write | Boolean | Require Azure Multi-Factor Authentication on eligible assignment \(True/False\) | - |
| ElegibilityAssignmentReqJustification | Write | Boolean | Require justification on eligible assignment \(True/False\) | - |
| EligibleAlertNotificationDefaultRecipient | Write | Boolean | Send notifications when members are assigned as eligible to this role: Role assignment alert, default recipient \(True/False\) | - |
| EligibleAlertNotificationAdditionalRecipient | Write | StringArray\[\] | Send notifications when members are assigned as eligible to this role: Role assignment alert, additional recipient \(UPN\) | - |
| EligibleAlertNotificationOnlyCritical | Write | Boolean | Send notifications when members are assigned as eligible to this role: Role assignment alert, only critical Email \(True/False\) | - |
| EligibleAssigneeNotificationDefaultRecipient | Write | Boolean | Send notifications when members are assigned as eligible to this role: Notification to the assigned user \(assignee\), default recipient \(True/False\) | - |
| EligibleAssigneeNotificationAdditionalRecipient | Write | StringArray\[\] | Send notifications when members are assigned as eligible to this role: Notification to the assigned user \(assignee\), additional recipient \(UPN\) | - |
| EligibleAssigneeNotificationOnlyCritical | Write | Boolean | Send notifications when members are assigned as eligible to this role: Notification to the assigned user \(assignee\), only critical Email \(True/False\) | - |
| EligibleApproveNotificationDefaultRecipient | Write | Boolean | Send notifications when members are assigned as eligible to this role: Request to approve a role assignment renewal/extension, default recipient \(True/False\) | - |
| EligibleApproveNotificationAdditionalRecipient | Write | StringArray\[\] | Send notifications when members are assigned as eligible to this role: Request to approve a role assignment renewal/extension, additional recipient \(UPN\) | - |
| EligibleApproveNotificationOnlyCritical | Write | Boolean | Send notifications when members are assigned as eligible to this role: Request to approve a role assignment renewal/extension, only critical Email \(True/False\) | - |
| ActiveAlertNotificationDefaultRecipient | Write | Boolean | Send notifications when members are assigned as active to this role: Role assignment alert, default recipient \(True/False\) | - |
| ActiveAlertNotificationAdditionalRecipient | Write | StringArray\[\] | Send notifications when members are assigned as active to this role: Role assignment alert, additional recipient \(UPN\) | - |
| ActiveAlertNotificationOnlyCritical | Write | Boolean | Send notifications when members are assigned as active to this role: Role assignment alert, only critical Email \(True/False\) | - |
| ActiveAssigneeNotificationDefaultRecipient | Write | Boolean | Send notifications when members are assigned as active to this role: Notification to the assigned user \(assignee\), default recipient \(True/False\) | - |
| ActiveAssigneeNotificationAdditionalRecipient | Write | StringArray\[\] | Send notifications when members are assigned as active to this role: Notification to the assigned user \(assignee\), additional recipient \(UPN\) | - |
| ActiveAssigneeNotificationOnlyCritical | Write | Boolean | Send notifications when members are assigned as active to this role: Notification to the assigned user \(assignee\), only critical Email \(True/False\) | - |
| ActiveApproveNotificationDefaultRecipient | Write | Boolean | Send notifications when members are assigned as active to this role: Request to approve a role assignment renewal/extension, default recipient \(True/False\) | - |
| ActiveApproveNotificationAdditionalRecipient | Write | StringArray\[\] | Send notifications when members are assigned as active to this role: Request to approve a role assignment renewal/extension, additional recipient \(UPN\) | - |
| ActiveApproveNotificationOnlyCritical | Write | Boolean | Send notifications when members are assigned as active to this role: Request to approve a role assignment renewal/extension, only critical Email \(True/False\) | - |
| EligibleAssignmentAlertNotificationDefaultRecipient | Write | Boolean | Send notifications when eligible members activate this role: Role assignment alert, default recipient \(True/False\) | - |
| EligibleAssignmentAlertNotificationAdditionalRecipient | Write | StringArray\[\] | Send notifications when eligible members activate this role: Role assignment alert, additional recipient \(UPN\) | - |
| EligibleAssignmentAlertNotificationOnlyCritical | Write | Boolean | Send notifications when eligible members activate this role: Role assignment alert, only critical Email \(True/False\) | - |
| EligibleAssignmentAssigneeNotificationDefaultRecipient | Write | Boolean | Send notifications when eligible members activate this role: Notification to activated user \(requestor\), default recipient \(True/False\) | - |
| EligibleAssignmentAssigneeNotificationAdditionalRecipient | Write | StringArray\[\] | Send notifications when eligible members activate this role: Notification to activated user \(requestor\), additional recipient \(UPN\) | - |
| EligibleAssignmentAssigneeNotificationOnlyCritical | Write | Boolean | Send notifications when eligible members activate this role: Notification to activated user \(requestor\), only critical Email \(True/False\) | - |
| AuthenticationContextRequired | Write | Boolean | Authorization context is required \(True/False\) | - |
| AuthenticationContextName | Write | String | Descriptive name of associated authorization context | - |
| AuthenticationContextId | Write | String | Authorization context id | - |
| Ensure | Write | String | Specify if the Microsoft Entra role setting should exist or not. | `Present` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Privileged Role Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Group.Read.All, RoleManagement.Read.Directory, User.Read.All, RoleManagementPolicy.Read.Directory |
| Update | Group.Read.All, RoleManagement.ReadWrite.Directory, User.Read.All, RoleManagementPolicy.ReadWrite.Directory |

## securityDefaults resource type

### Description

This resource configures the Security Defaults in Microsoft Entra.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes'. | `Yes` |
| DisplayName | Write | String | Display name of the security defaults. | - |
| Description | Write | String | Description of the security defaults. | - |
| IsEnabled | Write | Boolean | Represents whether or not security defaults are enabled. | - |
| Ensure | Write | String | Specify if the Microsoft Entra App should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Security Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.All |
| Update | Policy.ReadWrite.SecurityDefaults |

## servicePrincipal resource type

### Description

This resource configures an Microsoft Entra ServicePrincipal.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| AppId | Key | String | The unique identifier for the associated application. | - |
| AppRoleAssignedTo | Write | ServicePrincipalRoleAssignment\[\] | App role assignments for this app or service, granted to users, groups, and other service principals. | - |
| ObjectID | Write | String | The ObjectID of the ServicePrincipal | - |
| DisplayName | Write | String | Displayname of the ServicePrincipal. | - |
| AlternativeNames | Write | StringArray\[\] | The alternative names for this service principal | - |
| AccountEnabled | Write | Boolean | True if the service principal account is enabled; otherwise, false. | - |
| AppRoleAssignmentRequired | Write | Boolean | Indicates whether an application role assignment is required. | - |
| ErrorUrl | Write | String | Specifies the error URL of the ServicePrincipal. | - |
| Homepage | Write | String | Specifies the homepage of the ServicePrincipal. | - |
| LogoutUrl | Write | String | Specifies the LogoutURL of the ServicePrincipal. | - |
| PublisherName | Write | String | Specifies the PublisherName of the ServicePrincipal. | - |
| ReplyUrls | Write | StringArray\[\] | The URLs that user tokens are sent to for sign in with the associated application, or the redirect URIs that OAuth 2.0 authorization codes and access tokens are sent to for the associated application. | - |
| SamlMetadataUrl | Write | String | The URL for the SAML metadata of the ServicePrincipal. | - |
| ServicePrincipalNames | Write | StringArray\[\] | Specifies an array of service principal names. Based on the identifierURIs collection, plus the application's appId property, these URIs are used to reference an application's service principal. | - |
| ServicePrincipalType | Write | String | The type of the service principal. | - |
| Tags | Write | StringArray\[\] | Tags linked to this service principal.Note that if you intend for this service principal to show up in the All Applications list in the admin portal, you need to set this value to {WindowsAzureActiveDirectoryIntegratedApp} | - |
| Ensure | Write | String | Specify if the Microsoft Entra App should exist or not. | `Present`, `Absent` |

#### ServicePrincipalRoleAssignment

##### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| PrincipalType | Write | String | Type of principal. Accepted values are User or Group | `Group`, `User` |
| Identity | Write | String | Unique identity representing the principal. | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Application Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Application.Read.All, Group.Read.All, User.Read.All |
| Update | Application.ReadWrite.All, Group.Read.All, User.Read.All |

## socialIdentityProvider resource type

### Description

Represents identity providers with External Identities for both Microsoft Entra ID and Microsoft Entra B2C tenants. For Microsoft Entra B2B scenarios in a Microsoft Entra tenant, the identity provider type can be Google or Facebook.

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| ClientId | Key | String | The client identifier for the application obtained when registering the application with the identity provider. | - |
| ClientSecret | Write | String | The client secret for the application that is obtained when the application is registered with the identity provider. This is write-only. A read operation returns \*\*\*\*. | - |
| DisplayName | Write | String | The display name of the identity provider. | - |
| IdentityProviderType | Write | String | For a B2B scenario, possible values: Google, Facebook. For a B2C scenario, possible values: Microsoft, Google, Amazon, LinkedIn, Facebook, GitHub, Twitter, Weibo, QQ, WeChat. | `AADSignup`, `EmailOTP`, `Microsoft`, `MicrosoftAccount`, `Google`, `Amazon`, `LinkedIn`, `Facebook`, `GitHub`, `Twitter`, `Weibo`, `QQ`, `WeChat` |
| Ensure | Write | String | Present ensures the policy exists, absent ensures it's removed. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | Security Reader |
| Update | Authentication Policy Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | IdentityProvider.Read.All |
| Update | IdentityProvider.ReadWrite.All |

## tenantDetails resource type

### Description

This resource configures the Microsoft Entra Tenant Details

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| IsSingleInstance | Key | String | Only valid value is 'Yes'. | `Yes` |
| MarketingNotificationEmails | Write | StringArray\[\] | Email-addresses from the people who should receive Marketing Notifications | - |
| SecurityComplianceNotificationMails | Write | StringArray\[\] | Email-addresses from the people who should receive Security Compliance Notifications | - |
| SecurityComplianceNotificationPhones | Write | StringArray\[\] | Phone Numbers from the people who should receive Security Notifications | - |
| TechnicalNotificationMails | Write | StringArray\[\] | Email-addresses from the people who should receive Technical Notifications | - |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Billing Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Organization.Read.All |
| Update | Organization.ReadWrite.All |

## tokenLifetimePolicy resource type

### Description

This resource configures the Microsoft Entra Token Lifetime Policies

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| DisplayName | Key | String | DisplayName of the Policy | - |
| Id | Write | String | ObjectID of the Policy. | - |
| Description | Write | String | Description of the Policy. | - |
| Definition | Write | StringArray\[\] | Definition of the Policy. | - |
| IsOrganizationDefault | Write | Boolean | IsOrganizationDefault of the Policy. | - |
| Ensure | Write | String | Specify if the Microsoft Entra Policy should exist or not. | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | Application Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | Policy.Read.All |
| Update | Policy.ReadWrite.ApplicationConfiguration |

## user resource type

### Description

This resource allows users to create Microsoft Entra Users and assign them licenses, roles and/or groups.

When using AADGroup with AADUser, avoid specifying both AADUser->MemberOf and AADGroup->Member for the same group, as mismatched values can cause conflicts. Choose one approach. See AADGroup

### Parameters

| Parameter | Attribute | DataType | Description | Allowed Values |
| --- | --- | --- | --- | --- |
| UserPrincipalName | Key | String | The login name of the user | - |
| DisplayName | Write | String | The display name for the user | - |
| FirstName | Write | String | The first name of the user | - |
| LastName | Write | String | The last name of the user | - |
| Roles | Write | StringArray\[\] | The list of Microsoft Entra roles assigned to the user. | - |
| UsageLocation | Write | String | The country/region code the user is assigned to | - |
| LicenseAssignment | Write | StringArray\[\] | The account SKU Id for the license to be assigned to the user | - |
| Password | Write | PSCredential | The password for the account. The parameter is a PSCredential object, but only the Password component is used. When Password isn't supplied for a new resource a new random password is generated. Property is used when creating the user and not on subsequent updates. | - |
| City | Write | String | The City name of the user | - |
| Country | Write | String | The Country/region name of the user | - |
| Department | Write | String | The Department name of the user | - |
| Fax | Write | String | The Fax Number of the user | - |
| MemberOf | Write | StringArray\[\] | The Groups that the user is a direct member of | - |
| MobilePhone | Write | String | The Mobile Phone Number of the user | - |
| Office | Write | String | The Office Name of the user | - |
| PasswordNeverExpires | Write | Boolean | Specifies whether the user password expires periodically. Default value is false | - |
| PasswordPolicies | Write | String | Specifies password policies for the user. | - |
| PhoneNumber | Write | String | The Phone Number of the user | - |
| PostalCode | Write | String | The Postal Code of the user | - |
| PreferredLanguage | Write | String | The Preferred Language of the user | - |
| State | Write | String | Specifies the state or province where the user is located | - |
| StreetAddress | Write | String | Specifies the street address of the user | - |
| Title | Write | String | Specifies the title of the user | - |
| UserType | Write | String | Specifies the title of the user | `Guest`, `Member`, `Other`, `Viral` |
| Ensure | Write | String | Present ensures the user exists, absent ensures it's removed | `Present`, `Absent` |

### Permissions

#### Microsoft Entra ID roles

The following [roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=/graph/toc.json) can be granted to the TCM \(Tenant Configuration Management\) service principal:

| Operation | Least privileged role |
| --- | --- |
| Read | None |
| Update | User Administrator |

#### Microsoft Graph

To authenticate with the Microsoft Graph API, this resource requires the following application permissions. Delegated scenarios aren't supported. For more information about Microsoft Graph permissions, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

##### Application permissions

| Operation | Supported permissions |
| --- | --- |
| Read | RoleManagement.Read.Directory, User.Read.All |
| Update | Organization.Read.All, RoleManagement.ReadWrite.Directory, User.EnableDisableAccount.All, User.ReadWrite.All, Group.ReadWrite.All, GroupMember.ReadWrite.All |

## Related content

- [Overview of the Tenant Configuration Management APIs](https://learn.microsoft.com/en-us/graph/unified-tenant-configuration-management-concept-overview)
- [Set up authentication for TCM](https://learn.microsoft.com/en-us/graph/utcm-authentication-setup)
