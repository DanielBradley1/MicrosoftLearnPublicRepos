<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identity-network-access-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# Manage Microsoft Entra identity and network access capabilities by using Microsoft Graph

Microsoft Graph provides REST APIs to manage identity and network access capabilities, most of which are available through [Microsoft Entra](https://learn.microsoft.com/en-us/entra/fundamentals/whatis). These APIs help you automate identity and network access management tasks, integrate with applications, and serve as the programmatic alternative to administrator portals such as the Microsoft Entra admin center.

Microsoft Entra is a family of identity and network access solutions that includes the following products. All these capabilities are available through Microsoft Graph APIs:

- Microsoft Entra ID that groups identity and access management \(IAM\) capabilities.
- Microsoft Entra ID Governance
- Microsoft Entra External ID
- Microsoft Entra Verified ID
- Microsoft Entra Permissions Management \(deprecated\)
- Microsoft Entra Internet Access and Network Access

## Manage user identities

Users are the main identities in any identity and access solution. You can manage the entire lifecycle of users in your organization, including guests, and their entitlements like licenses or group memberships, using Microsoft Graph APIs. For more information, see [Working with users in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/users).

## Manage groups

Groups are the containers that allow you to efficiently manage the entitlements for identities as a unit. For example, through a group, you can grant users access to a resource, such as a SharePoint site. Or you can grant them licenses to use a service. For more information, see [Working with groups in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/groups-overview).

## Manage applications

You can use Microsoft Graph APIs to register and manage your applications programmatically, enabling you to use Microsoft's IAM capabilities. For more information, see [Manage Microsoft Entra applications and service principals by using Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/applications-api-overview).

## Manage agents

AI agents require the same identity, access, security, and governance frameworks that are applied to users, applications, and devices in your organization. Microsoft Graph APIs support the full agent identity lifecycle, including:

- **Creating and managing agent identities** - Programmatically create and manage agent identity blueprints, agent identities, and their associated metadata such as owners and sponsors.
- **Security and access control** - Apply Conditional Access policies to enforce access controls on agents, and use entitlement management access packages to assign agents access to security groups, application permissions, and Microsoft Entra roles.
- **Governance** - Assign sponsors to agent identities to maintain human accountability over the agent lifecycle. Use access reviews to periodically validate that agent identities still need their assigned access.
- **Risk detection and monitoring** - Monitor agent sign-in activities through audit logs for compliance and security purposes.

For more information about using Microsoft Graph APIs to achieve these capabilities for agents, see [Microsoft Entra Agent ID APIs in Microsoft Graph overview](https://learn.microsoft.com/en-us/graph/api/resources/agentid-platform-overview).

---

## Tenant administration and directory management

A core functionality of identity and access management is managing your tenant configuration, administrative roles, and settings. Microsoft Graph provides APIs to manage your Microsoft Entra tenant for the following scenarios:

| Use cases | API operations |
| --- | --- |
| Manage administrative units including the following operations:<br><br>- Create administrative units<br>- Create and manage members and membership rules of administrative units<br>- Assign administrator roles that are scoped to administrative units | [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit) and its associated APIs |
| Retrieve BitLocker recovery keys | [bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey) and its associated APIs |
| Manage custom security attributes | See [Overview of custom security attributes using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/api/resources/custom-security-attributes-overview) |
| Back up and restore critical directory objects to a previously known good state, including users, groups, applications, service principals, and conditional access policies, helping you recover from accidental changes or security compromises  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | See [Overview of Microsoft Entra Backup and Recovery APIs](https://learn.microsoft.com/en-us/graph/api/resources/entrarecoveryservices-backup-recovery-overview) |
| Manage deleted directory objects. The functionality to store deleted objects in a "recycle bin" is supported for the following objects:<br><br>- Administrative units<br>- Applications<br>- External user profiles  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png)<br>- Groups<br>- Pending external user profiles  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png)<br>- Service principals<br>- Users | - [Get](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get) or [List](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list) deleted objects<br>- [Permanently delete](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-delete) a deleted object<br>- [Restore a deleted item](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore)<br>- [List deleted items owned by user](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-getuserownedobjects) |
| Manage devices in the cloud | - [device](https://learn.microsoft.com/en-us/graph/api/resources/device) and its associated APIs<br>- ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) [deviceTemplate](https://learn.microsoft.com/en-us/graph/api/resources/devicetemplate) and its associated APIs |
| View local administrator credential information for all device objects in Microsoft Entra ID that are enabled with Local Admin Password Solution \(LAPS\). This feature is the cloud-based LAPS solution | [deviceLocalCredentialInfo](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredentialinfo) and its associated APIs |
| Directory objects are the core objects in Microsoft Entra ID, such as users, groups, and applications. You can use the directoryObject resource type and its associated APIs to check memberships of directory objects, track changes for multiple directory objects, or validate that a Microsoft 365 group's display name or mail nickname complies with naming policies | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject) and its associated APIs |
| Manage administrator roles including the following operations:<br><br>- Create custom roles<br>- Assign roles to users, groups, or service principals<br>- Track changes to role assignments<br>- Remove assignees from roles | The following resources and their associated APIs:<br><br>- [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole) and [directoryRoleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/directoryroletemplate)<br>- [roleManagement](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagement) \(**recommended**\)<br><br>  <br>  <br>For just-in-time and time-bound role assignments instead of direct forever active assignments, use Privileged Identity Management APIs for [Microsoft Entra roles](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagementv3-overview) and [groups](https://learn.microsoft.com/en-us/graph/api/resources/privilegedidentitymanagement-for-groups-api-overview) |
| Define the following configurations that can be used to customize the tenant-wide and object-specific restrictions and allowed behavior.<br><br>- Settings for Microsoft 365 groups such as guest user access, classifications, and naming policies<br>- Password rule settings such as banned password lists and lockout duration<br>- Prohibited names for applications, reserved words, and blocking trademark violations<br>- Custom conditional access policy URL<br>- Consent policies such as user consent requests, group-specific consent, and consent for risky apps | In `beta`: [directorySetting](https://learn.microsoft.com/en-us/graph/api/resources/directorysetting) and [directorySettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/directorysettingtemplate) and their associated APIs  <br>In `v1.0`: [groupSetting](https://learn.microsoft.com/en-us/graph/api/resources/groupsetting) and [groupSettingTemplate](https://learn.microsoft.com/en-us/graph/api/resources/groupsettingtemplate) and their associated APIs  <br>  <br>For more information, see [Overview of group settings](https://learn.microsoft.com/en-us/graph/group-directory-settings). |
| Domain management operations such as:<br><br>- associating a domain with your tenant<br>- retrieving DNS records<br>- verifying domain ownership<br>- External admin takeover of unmanaged domains<br>- associating specific services with specific domains<br>- deleting domains | [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain) and its associated APIs |
| Manage the profile objects for external users that you're invited to collaborate via Teams. These APIs aren't similar to the invitation APIs for Microsoft Entra External ID B2B collaboration  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | [externalUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/externaluserprofile) and [pendingExternalUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/externaluserprofile) and their associated APIs |
| Configure and manage staged rollout of specific Microsoft Entra ID features | [featureRolloutPolicy](https://learn.microsoft.com/en-us/graph/api/resources/featurerolloutpolicy) and its associated APIs |
| Monitor licenses and subscriptions for the tenant | - [companySubscription](https://learn.microsoft.com/en-us/graph/api/resources/companysubscription) and its associated APIs<br>- [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku) and its associated APIs |
| Manage the policies for Mobile Device Management \(MDM\) and Mobile Application Management \(MAM\) autoenrollment for Microsoft Entra joined and registered devices  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | The following resources and their associated APIs:<br><br>- [mobileAppManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobileappmanagementpolicy)<br>- [mobileDeviceManagementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/mobiledevicemanagementpolicy) |
| Configure options that are available in Microsoft Entra Cloud Sync such as preventing accidental deletions and managing group writebacks. | [onPremisesDirectorySynchronization](https://learn.microsoft.com/en-us/graph/api/resources/onpremisesdirectorysynchronization) and its associated APIs |
| Manage synchronization settings for directory objects such as users, groups, and organizational contacts between on-premises Active Directory and the cloud  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | [onPremisesSyncBehavior](https://learn.microsoft.com/en-us/graph/api/resources/onpremisessyncbehavior) and its associated APIs |
| Manage the base settings for your Microsoft Entra tenant | [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization) and its associated APIs |
| Manage the tenant-wide settings for your Microsoft Entra tenant, such as whether people and item insights are enabled for the organization  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | [organizationSettings](https://learn.microsoft.com/en-us/graph/api/resources/organizationsettings) and its associated APIs |
| Retrieve the organizational contacts that might be synchronized from on-premises directories or from Exchange Online | [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact) and its associated APIs |
| Discover the basic details of other Microsoft Entra tenants by querying using the tenant ID or the domain name | [tenantInformation](https://learn.microsoft.com/en-us/graph/api/resources/tenantinformation) and its associated APIs |

---

## Identity and sign-in

| Use cases | API operations |
| --- | --- |
| Grant, revoke, and retrieve app roles on a resource application for users, groups, or service principals | [appRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/approleassignment) and its associated APIs |
| Configure listeners that monitor events that should trigger or invoke custom logic, typically defined outside Microsoft Entra ID | [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener) and its associated APIs |
| Manage authentication methods that are supported in Microsoft Entra ID | See [Microsoft Entra authentication methods API overview](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-overview) and [Microsoft Entra authentication methods policies API overview](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodspolicies-overview) |
| Manage the authentication methods or combinations of authentication methods that you can apply as grant control in Microsoft Entra Conditional Access | See [Microsoft Entra authentication strengths API overview](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengths-overview) |
| Manage tenant-wide authorization policies such as:<br><br>- enable SSPR for administrator accounts<br>- enable self-service join for guests<br>- limit who can invite guests<br>- whether users can consent to risky apps<br>- block the use of MSOL<br>- customize the default user permissions<br>- identity private preview features enabled<br>- Customize the guest user permissions between *User*, *Guest User*, and *Restricted Guest User* | [authorizationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authorizationpolicy) and its associated APIs |
| Customize the UI/UX in Azure AD B2C using the Identity Experience Framework \(IEF\)  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | [trustFrameworkKeySet](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkkeyset) and [trustFrameworkPolicy](https://learn.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy) and their associated APIs |
| Manage the policies for certificate-based authentication in the tenant | [certificateBasedAuthConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthconfiguration) and its associated APIs |
| Manage Microsoft Entra Conditional Access policies, including network locations such as countries, IP addresses, and compliant networks  <br>Evaluate the impact of Conditional Access policies before enforcing them  <br>Configure Continuous Access Evaluation \(CAE\), which allows access tokens to be revoked based on critical events and policy evaluation rather than relying on token expiry based on lifetime  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | The following resources and their associated APIs:<br><br>- [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy)<br>- [conditionalAccessTemplate](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesstemplate)<br>- [authenticationContextClassReference](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcontextclassreference)<br>- [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation)<br>- [whatIfAnalysisResult](https://learn.microsoft.com/en-us/graph/api/resources/whatifanalysisresult)<br>- [continuousAccessEvaluationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/continuousaccessevaluationpolicy) |
| Manage cross-tenant access settings and manage outbound restrictions, inbound restrictions, tenant restrictions, and cross-tenant synchronization of users in multitenant organizations | See [Cross-tenant access settings API overview](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantaccesspolicy-overview) |
| Manage the user profiles that are shared with you or external tenants using B2B direct connect, including removing and exporting personal data  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | [inboundSharedUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/inboundshareduserprofile) and [outboundSharedUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/outboundshareduserprofile) and their associated APIs |
| Configure how and which external systems interact with Microsoft Entra ID during a user authentication session | [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension) and its associated APIs |
| Manage requests against user data in the organization, such as exporting personal data | [dataPolicyOperation](https://learn.microsoft.com/en-us/graph/api/resources/datapolicyoperation) and its associated APIs |
| Configure the policies for managing Microsoft Entra join and Microsoft Entra register devices  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | [deviceRegistrationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/deviceregistrationpolicy) and its associated APIs |
| Manage the tenant-wide policy that controls whether external users can leave a Microsoft Entra tenant via self-service controls, for example, through the **organizations** menu of the **My Account** portal  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | [externalIdentitiesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/externalidentitiespolicy) and its associated APIs |
| Force autoacceleration sign-in to skip the username entry screen and automatically forward users to federated sign-in endpoints | [homeRealmDiscoveryPolicy](https://learn.microsoft.com/en-us/graph/api/resources/homerealmdiscoverypolicy) and its associated APIs |
| Detect, investigate, and remediate identity-based risks using Microsoft Entra ID Protection and feed the data into security information and event management \(SIEM\) tools for further investigation and correlation | See [Use the Microsoft Graph identity protection APIs](https://learn.microsoft.com/en-us/graph/api/resources/identityprotection-overview) |
| Manage identity providers for Microsoft Entra ID, Microsoft Entra External ID, and Azure AD B2C tenants. You can perform the following operations:<br><br>- Manage identity providers for external identities, including social identity providers, OIDC, Apple, SAML/WS-Fed, and built-in providers<br>- Manage configuration for federated domains and token validation | [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase) and its associated APIs |
| Define a group of tenants belonging to your organization and streamline intra-organization cross-tenant collaboration | See [Multitenant organization API overview](https://learn.microsoft.com/en-us/graph/api/resources/multitenantorganization-overview) |
| Manage the delegated permissions and their assignments to service principals in the tenant | [oAuth2PermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/oauth2permissiongrant) and its associated APIs |
| Customize sign-in UIs to match your company branding, including applying branding that's based on the browser language | [organizationalBranding](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding) and its associated APIs |
| Configure trusted certificate authorities for certificates that can be assigned to apps and service principals in the tenant. | [certificateBasedApplicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedapplicationconfiguration) and its associated APIs |
| User flows for Microsoft Entra External ID in workforce tenants | the following resources and their associated APIs:<br><br>- [b2xIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2xidentityuserflow) to configure the base user flow and its properties such as identity providers<br>- [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute) to manage built-in and custom user flow attributes<br>- [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment) to manage user flow attribute assignments<br>- [userFlowLanguageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguageconfiguration) to configure custom languages for user flows |
| User flows for Azure AD B2C  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | the following resources and their associated APIs:<br><br>- [b2cIdentityUserFlow](https://learn.microsoft.com/en-us/graph/api/resources/b2cidentityuserflow) to configure the base user flow and its properties such as identity providers<br>- [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute) to manage built-in and custom user flow attributes<br>- [identityUserFlowAttributeAssignment](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattributeassignment) to manage user flow attribute assignments<br>- [userFlowLanguageConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguageconfiguration) to configure custom languages for user flows |
| User flows for Microsoft Entra External ID in external tenants | the following resources and their associated APIs:<br><br>- [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow) and its associated APIs<br>- [identityUserFlowAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute) to manage built-in and custom user flow attributes |
| Manage app consent policies and condition sets | [permissionGrantPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpolicy) |
| Manage app consent preapproval policies  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | [permissionGrantPreApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/permissiongrantpreapprovalpolicy) |
| Enable or disable security defaults in Microsoft Entra ID | [identitySecurityDefaultsEnforcementPolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitysecuritydefaultsenforcementpolicy) |

---

## Identity governance

For more information, see [Overview of Microsoft Entra ID Governance using Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-overview).

## Microsoft Entra External ID in external tenants

The following API use cases are supported to customize how users interact with your customer-facing applications. For administrators, most of the features available in Microsoft Entra ID and also supported for Microsoft Entra External ID in external tenants. For example, domain management, application management, and conditional access. For more information about all features supported in External ID, see [Supported features in workforce and external tenants](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers).

| Use cases | API operations |
| --- | --- |
| User flows for Microsoft Entra External ID in external tenants and self-service sign-up experiences | [authenticationEventsFlow](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventsflow) and its associated APIs |
| Manage identity providers for Microsoft Entra External ID. You can identify the identity providers that are supported or configured in the tenant | See [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase) and its associated APIs |
| Configuring custom URL domains in Microsoft Entra External ID in external tenants | The `CustomUrlDomain` value for the **supportedServices** property of [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain) and its associated APIs |
| Customize sign-in UIs to match your company branding, including applying branding that's based on the browser language or to apply app-based branding  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | [organizationalBranding](https://learn.microsoft.com/en-us/graph/api/resources/organizationalbranding) and its associated APIs |
| Manage identity providers for Microsoft Entra External ID, such as social identities | [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase) and its associated APIs |
| Sign in with an alias or username  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | [signInIdentifierBase](https://learn.microsoft.com/en-us/graph/api/resources/signinidentifierbase) and its associated APIs |
| Manage user profiles in Microsoft Entra External ID for customers | For more information, see [Default user permissions in customer tenants](https://learn.microsoft.com/en-us/graph/api/resources/users#default-user-permissions-in-customer-tenants) |
| Manage Microsoft Entra Conditional Access policies, such as including all users, or excluding specific users and groups  <br>Targeting resources and authentication context  <br>Applying conditions such as device platforms and network locations such as countries, IP addresses, and compliant networks  <br>Session controls \(Sign-in frequency and Persistent browser session\) | The following resources and their associated APIs:<br><br>- [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy)<br>- [authenticationContextClassReference](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcontextclassreference)<br>- [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation) |
| Add your own business logic to the authentication experiences by integrating with systems that are external to Microsoft Entra ID | [authenticationEventListener](https://learn.microsoft.com/en-us/graph/api/resources/authenticationeventlistener) and [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension) and their associated APIs |
| Integrate with fraud protection providers to prevent fake account sign-ups and bot attacks during the user sign-up process. Supported providers include Arkose Labs and HUMAN Security | [fraudProtectionProvider](https://learn.microsoft.com/en-us/graph/api/resources/fraudprotectionprovider) and [onFraudProtectionLoadStartListener](https://learn.microsoft.com/en-us/graph/api/resources/onfraudprotectionloadstartlistener) and their associated APIs |
| Integrate with Web Application Firewall providers such as Akamai and Cloudflare | [webApplicationFirewallProvider](https://learn.microsoft.com/en-us/graph/api/resources/webapplicationfirewallprovider) and its associated APIs |

## Multicloud permissions management \(deprecated\)

![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png)

For more information, see [Discover, remediate, and monitor permissions in multicloud infrastructures using permissions management APIs](https://learn.microsoft.com/en-us/graph/api/resources/permissions-management-api-overview).

## Network access management

![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png)

For more information, see [Secure access to cloud, public, and private apps using Microsoft Graph network access APIs](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-global-secure-access-api-overview).

## Partner tenant management

Microsoft Graph also provides the following identity and access capabilities for Microsoft partners in the Cloud Solution Provider \(CSP\), Value Added Reseller \(VAR\), or Advisor programs to help manage their customer tenants.

| Use cases | API operations |
| --- | --- |
| Manage contracts for the partner with its customers | [contract](https://learn.microsoft.com/en-us/graph/api/resources/contract) and its associated APIs |
| Microsoft partners can empower their customers to ensure the partners have least privileged access to their customers' tenants. This feature gives extra control to customers over their security posture while allowing them to receive support from the Microsoft resellers | See [Granular delegated admin privileges \(GDAP\) API overview](https://learn.microsoft.com/en-us/graph/api/resources/delegatedadminrelationships-api-overview) |
| Get detections and security alerts for unauthorized party abuse, account takeovers, and anomalous usage of Azure subscriptions in the customer tenants that you're responsible for.  ![Available on beta only.](https://learn.microsoft.com/en-us/graph/images/preview-label.png) | See [Use the partner security alert API in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/partner-security-partnersecurityalert-api-overview) |

## Identity and access reports

Microsoft Entra records *every* activity in your tenant and produces reports and audit logs that you can analyze for monitoring, compliance, and troubleshooting. Records of these activities are also available through Microsoft Graph reporting and audit logs APIs, which allow you to analyze the activities with Azure Monitor logs and Log Analytics, or stream to third-party SIEM tools for further investigations. For more information, see [Identity and access reports API overview](https://learn.microsoft.com/en-us/graph/api/resources/report-identity-access).

---

## Zero Trust

This feature helps organizations to align their tenants with the three guiding principles of a Zero Trust architecture:

- Verify explicitly
- Use least privilege
- Assume breach

To find out more about Zero Trust and other ways to align your organization to the guiding principles, see the [Zero Trust Guidance Center](https://learn.microsoft.com/en-us/security/zero-trust/).

## Licensing

Microsoft Entra licenses include Microsoft Entra ID Free, P1, P2, and Governance; Microsoft Entra Permissions Management; and Microsoft Entra Workload ID.

For detailed information about licensing for different features, see [Microsoft Entra ID licensing](https://learn.microsoft.com/en-us/entra/fundamentals/licensing).

## Related content

- [Implement identity standards with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/standards/)
- [Microsoft Entra ID Guide for independent software developers](https://learn.microsoft.com/en-us/entra/architecture/guide-for-independent-software-developers)
- Review the [Microsoft Entra deployment plans](https://learn.microsoft.com/en-us/entra/architecture/deployment-plans) to help you build your plan to deploy the Microsoft Entra suite of capabilities.
