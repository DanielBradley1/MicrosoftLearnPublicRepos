<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/design-tenant-configurations -->
<!-- Sitemap-Last-Modified: 2026-02-11 -->

# Design Tenant Configuration

Configuration in Microsoft Entra ID is done within each tenant. Configuration settings control your security and access policies. Document your security and access policies to ensure consistency across tenants where applicable.

## Configuration consistency across tenants

In a large education environment where you have a central administration team, ensuring that most configurations are consistent across tenants will:

- Simplify management and make your Central IT team more efficient.
- Make it easier to identify and troubleshoot issues.
- Make it easier to develop, test, and deploy software across tenants.
- Make the user experience across tenants more consistent and intuitive.
- Ease the process of migrating users from one tenant to another.

Create policies on which tenant configurations are standard and managed by your central IT team, and which can be adjusted by the tenant-specific IT team. Some areas where a tenant-specific administration team may need to have flexibility include:

- Allowing external partners to access the tenant. While your organization may have a policy that only allows its other tenants access, a specific region may need a region-specific vendor to the Microsoft Entra B2B collaboration Allow list.
- Adjusting the required access policies, for example requiring managed devices to meet tenant- or region-specific security requirements, or to account for the availability of managed devices.
- Piloting new features, for example a region trying out [MyStaff](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/my-staff-configure) to let a school's director cover certain IT tasks for the staff at that school.

## Configure external identities

External identities represent users from outside a Microsoft Entra tenant, such as users from other tenants in the EDU organization. In a large EDU organization that spans multiple tenants, you can use [Microsoft Entra business-to-business \(B2B\) collaboration](https://learn.microsoft.com/en-us/azure/active-directory/b2b/what-is-b2b) to provide access across those tenants. Microsoft Entra B2B lets you securely share your organization’s applications and services with guests from another organization, while maintaining control over your own data.

### Control external collaboration

[External collaboration settings](https://learn.microsoft.com/en-us/azure/active-directory/b2b/delegate-invitations) let you turn guest invitations on or off for different types of users in your organization. You can also delegate invitations to individual users by assigning roles that allow them to invite guests. External collaboration settings are managed in the Microsoft Entra admin center under Microsoft Entra ID.

## Enable guests to appear in the Global Address List

You can display guests \(external users\) in your Global Address List \(GAL\) by either:

- Inviting users as guests using Microsoft Entra B2B \(Recommended\)
- Using GAL Synchronization \(Not recommended\)

Note

GAL synchronization doesn't create user accounts. Rather, each contact it creates is an object that is counted against your object limit in the tenant.

## Security and access policies

Managing security can be difficult with identity-related attacks being so prevalent. Security defaults and access policies make it easier to help protect your organization from attacks such as password spray, replay, and phishing.

### Security defaults

[Security Defaults](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) provide secure settings that we manage on behalf of your organization to keep you safe until you're ready to manage your own identity security story. When security defaults are enabled, we can help you protect your organization with the following preconfigured policy settings:

- Requiring all users to register for Azure Multi-Factor Authentication
- Requiring administrators to perform multi-factor authentication
- Blocking legacy authentication protocols
- Requiring users to perform multi-factor authentication when necessary
- Protecting privileged activities like access to the Azure portal

Enabling security defaults is recommended if your organization wants to increase your security posture now, and you haven't configured robust security. If you're an organization with Microsoft Entra ID P1 or P2 licenses and are currently using Conditional Access policies to enforce organizational policies, security defaults are probably not right for you.

Enable Security defaults in the Azure portal as shown in the following image.

![Screenshot of the Azure portal with the toggle to enable security defaults.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-tenant-configurations-1.png)

### Managed devices for IT and staff

To protect resources in your tenant, prevent access by devices with unknown protection levels. Implement a device management solution so that users are only able to access resources using a device that is managed by the organization.

In Microsoft Entra ID, a minimum requirement for a device to be considered managed is when it's registered with Microsoft Entra ID. Admins can choose to implement the following types of device management in Microsoft Entra ID:

- Hybrid Domain Joined. Devices that are owned by the organization and [joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/concept-azure-ad-join-hybrid) to both the on-premises Active Directory and Microsoft Entra ID. Typically a device purchased and managed by an organization and managed by System Center Configuration Manager.
- Microsoft Entra Domain Joined. Devices that are owned by the organization and joined to the organization’s Microsoft Entra tenant. Usually a device purchased and managed by an organization, joined to Microsoft Entra ID, and managed by a service such as [Microsoft Intune](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune).
- Microsoft Entra registered. Devices owned by the organization, or personal devices, used to access company resources. Usually a personal device used to access corporate resources. Organizations may require the device be enrolled via [Mobile Device Management \(MDM\)](https://www.microsoft.com/itshowcase/mobile-device-management-at-microsoft), or enforced through [Mobile Application Management \(MAM\)](https://learn.microsoft.com/en-us/office365/enterprise/office-365-client-support-mobile-application-management) without enrollment to access resources. This capability can be provided by a service such as Microsoft Intune.

To learn more, see [Choose your integration methods](https://learn.microsoft.com/en-us/azure/active-directory/devices/plan-device-deployment).

To further enhance security, we also recommend that you create an [Microsoft Entra Conditional Access](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/require-managed-devices) policy for IT and staff. With Conditional Access, you can create a single policy that grants access:

- To selected cloud apps.
- For selected users and groups.
- Requiring a managed device.

### Use MFA for admins

Accounts that are assigned elevated permissions are valuable targets for attackers. To minimize the risk of privileged account compromise, provision all accounts with elevated permissions with strong authentication credentials such as [Azure Multi-Factor Authentication \(MFA\)](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-mfa-howitworks).

At a minimum, we recommend that you [create a Conditional Access policy to require MFA](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) for the following administrative roles:

- Billing administrator
- Conditional Access administrator
- Exchange administrator
- Global administrator
- Helpdesk \(password\) administrator
- Security administrator
- SharePoint administrator
- User administrator

If users have a multi-factor authentication method available to them, enforce MFA for users that have access to sensitive information like student records.

### Risk policies

With Microsoft Entra ID, admins can create policies to protect against [certain types of risks](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/concept-identity-protection-risks):

- Sign-in risk. The probability that a given authentication request isn't authorized by the identity owner.
- User risk. The probability that a given identity or account is compromised.

Sign-in risk policies and user risk policies automate the response to risk detections in your environment, and allow users to self-remediate risk.

Educational organizations with Microsoft 365 A5 licenses \(or Microsoft Entra ID P2 licenses\) can use [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/concept-identity-protection-policies) to secure their accounts. You can also create [sign-in risk-based Conditional Access policies](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-risk) and [user risk-based Conditional Access policies](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

Configure user risk policy so that [high-risk users](https://learn.microsoft.com/en-us/microsoft-365/enterprise/identity-access-policies) are required to change their password after sign-in.

### Best practices

- Define Conditional Access policies to enforce identity security posture by and minimize sign-in risks and user risks. This should include controls on MFA and device-based controls to enable access only through managed devices and expected locations.
- All applications should have explicit Conditional Access policies applied.
- Minimize the number of Conditional Access policies by applying to multiple apps with the same requirements.
- Plan for disruption by setting up [emergency access accounts](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-emergency-access) to mitigate the effects of accidental lockout.
- Configure a Conditional Access policy in [report-only mode](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/concept-conditional-access-report-only).

For general guidance on Conditional Access policies for individual environments, check the [CA Best practices](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/overview) and [Microsoft Entra Operations Guide](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-ops-guide-auth):

## App registrations

Only users with elevated permissions can perform tasks such as adding applications to the application gallery or configuring an application to use Application Proxy. However, by default, all users in your directory have the ability to register application and service principal objects. They also have discretion over which applications can access their organization data through user consent.

We recommend that you [disable user consent](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/configure-user-consent) so that nonprivileged accounts can't create application and service principal objects in the tenant. Instead [delegate team members application administration roles](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/roles-delegate-app-roles) such as the Application Administrator, Application Developer, or the Cloud Application Administrator roles. Using roles centralizes the decision-making process around consent with your organization’s security and identity teams.

### App integration

When possible, integrate supported SaaS applications using the [Microsoft Entra application gallery](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/tutorial-list) where you can find preconfigured apps that work with Microsoft Entra ID. If your application isn't available in the Microsoft Entra application gallery, you can [add the unlisted application](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/add-non-gallery-app) in the Microsoft Entra admin center.

In hybrid environments, you can enable secure remote access to your legacy applications using [Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy). Application proxy enables users to access on-premises web apps without a VPN using their Microsoft Entra account.

Alternatively, you can secure access to legacy apps if you're currently using any of the following third-party application delivery or network solutions:

- [Akamai Enterprise Application Access \(EAA\)](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/akamai-tutorial)
- [Citrix Application Delivery Controller \(ADC\)](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/citrix-netscaler-tutorial)
- [F5 Big-IP APM](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/headerf5-tutorial)
- [Zscaler Private Access \(ZPA\)](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/zscalerprivateaccess-tutorial)

## Design tenant security

In addition to the recommendations above, we also recommend that you lock down your tenant further by configuring the following settings in the Microsoft Entra admin center.

### User settings

| Setting | Value | Reason |
| --- | --- | --- |
| **Administration portal** |  |  |
| Restrict access to Microsoft Entra administration portal | Yes | This setting blocks non-privileged accounts from accessing the Microsoft Entra ID section of the Azure portal. |
| LinkedIn account connections | No | No business need |
| App registrations |  |  |
| Users can register applications | No | For educational organizations Microsoft recommends preventing non-privileged accounts to create application and service principal objects in the tenant. Instead, assign team members explicitly to application administration roles such as the Application Administrator, Application Developer or the Cloud Application Administrator roles. |

### External identities settings

| Setting | Value | Reason |
| --- | --- | --- |
| **Only allow tenants from same organization** |  |  |
| Guest permissions are limited | No | Guests come from well-known tenants. |
| Admins and users in the guest inviter role can invite | Yes | Guest invitation can be delegated when invitations are only allowed to specified domains. |
| Members can invite, Guests can invite | No | More control over who is invited into the tenant by only allowing certain administrators or administrators/users with the guest inviter role to invite guests. |
| Enable Email One-Time Passcode for guests \(Preview\) | No | Guests come from well-known tenants. |
| Enable guest self-service sign-up via user flows \(Preview\) | No | Invitations are only allowed to specified domains and user accounts are Microsoft Entra accounts in those other tenants. |
| Collaboration restrictions – Allow invitations only to the specified domains | Most restrictive | Microsoft recommends this setting for large organizations with multiple tenants that use the B2B collaboration features to provide access between the tenants.  <br>When you set your collaboration settings to Allow invitation only to specified domains \(most restrictive\), you include all domains that are part of your organization to the [allowlist](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/allow-deny-list), which will automatically deny invitations to any other domains. Or, if your school has a partnership with other organizations, you can restrict invitations to only those organizations by adding them to the allowlist. |
| **Allow collaboration outside own organization** |  |  |
| Guest permissions are limited | Yes | Guests can be from outside the own organization. This setting limits them from certain directory tasks like enumerating users, groups, or other directory objects. |
| Admins and users in the guest inviter role can invite | No | We recommend keeping invitations controlled with a group of delegated administrators when collaboration restrictions are set to allow invitation to be sent to any domain. |
| Members can invite, Guests can invite | No | More control over who is invited into the tenant by only allowing certain administrators or administrators/users with the guest inviter role to invite guests. |
| Enable Email One-Time Passcode for guests \(Preview\) | Yes | OTP is recommended when inviting users from outside your own organization. |
| Enable up guest self-service sign via user flows \(Preview\) | No | It's preferred to control invitations over letting guests self-service sign up to the tenant. |
| Collaboration restrictions – Allow invitations to be sent to any domain | Most inclusive | Recommended setting when there's a need to collaborate with multiple other tenants, for example, when collaborating with partners, external consultants, other educational organizations etc. |

### User feature previews settings

| Setting | Value | Reason |
| --- | --- | --- |
| Users can use preview feature for My Apps | None/Selected/All | Setting depends on use and need for My Apps portal and its features. You can consider using the My Apps portal to provide access to your organization’s cloud-based apps to only staff or to everyone including students. |
| Users can use the combined security information registration experience | All | It's recommended to use enhanced authentication methods such as passwordless credentials, and conditional access for securing security info registration. |
| Administrators can access My Staff | None/Selected/All | Setting depends on use and need for My Staff. You can consider using My Staff to delegate common helpdesk tasks to staff.  <br>My Staff enables you to delegate to a figure of authority, such as a school director, the permissions to ensure that their staff members are able to access their Microsoft Entra accounts. Instead of relying on a central helpdesk, organizations can delegate common tasks such as resetting passwords or changing phone numbers to, for example, a school director. With My Staff, a user who can't access their account can regain access in just a couple of select with no helpdesk or IT staff required. |

### Group management settings

| Setting | Value | Reason |
| --- | --- | --- |
| **Self-service group management** |  |  |
| Owners can manage group membership requests in the Access Panel | No | Groups in EDU tenants might have sensitive resource access \(for example, access to student information\) that should be structured and governed. User-initiated management isn't recommended for these scenarios. |
| Restrict user ability to access groups features in the Access Panel. Administrators \(Global, Group, and User Admin\) will have access regardless of the value of this setting | Yes | Groups in EDU tenants might have sensitive resource access \(for example, access to student information\) that should be structured and governed. User-initiated management isn't recommended for these scenarios. |
| Security groups |  |  |
| Users can create security groups in Azure portals | No | Groups in EDU tenants might have sensitive resource access \(for example, access to student information\) that should be structured and governed. User-initiated management isn't recommended for these scenarios |
| Owners who can assign members as group owners in Azure portals | None | Groups in EDU tenants might have sensitive resource access \(for example, access to student information\) that should be structured and governed. User-initiated management isn't recommended for these scenarios |
| Office 365 groups |  |  |
| Users can create Office 365 groups in Azure portals | No | Groups in EDU tenants might have sensitive resource access \(for example, access to student information\) that should be structured and governed. User-initiated management isn't recommended for these scenarios |
| Owners who can assign members as group owners in Azure portals | None | Groups in EDU tenants might have sensitive resource access \(for example, access to student information\) that should be structured and governed. User-initiated management isn't recommended for these scenarios |

### Enterprise applications settings

| Setting | Value | Reason |
| --- | --- | --- |
| **Enterprise applications** |  |  |
| Users can consent to apps accessing company data on their behalf | No | Applications that require consent should be reviewed through a defined process with established ownership using Admin Consent Request Workflows |
| Users can consent to apps accessing company data for the groups they own | No | Applications that require consent should be reviewed through a defined process with established ownership using Admin Consent Request Workflows |
| Users can add gallery apps to their Access Panel | No | Groups in EDU tenants might have sensitive resource access \(for example, access to student information\) that should be structured and governed. User-initiated management isn't recommended for these scenarios |
| Admin consent requests \(Preview\) |  |  |
| Users can request admin consent to apps they're unable to consent to​ | No | Enabling this setting gives all the users in your tenant the ability to request consent, potentially leading to many consent requests sent to admins. If admins can't or don't want to manage the requests, users can be confused. |
| Select users to review admin consent requests​ | N/A | Only applicable if Admin Consent Request feature is enabled |
| Selected users receive email notifications for requests​ | N/A | Only applicable if Admin Consent Request feature is enabled |
| Selected users receive request expiration reminders​ | N/A | Only applicable if Admin Consent Request feature is enabled |
| Consent request expires after \(days\) | N/A | Only applicable if Admin Consent Request feature is enabled |
| Office 365 Settings |  |  |
| Users can only see Office 365 apps in the Office 365 portal | No | When using My Apps portal this setting should be set to ‘No’ if you want Office 365 apps to show in My Apps. [My Apps portal overview](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/access-panel-deployment-plan)[apps/access-panel-deployment-plan](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/access-panel-deployment-plan) |

### Identity governance settings

Manage the lifecycle of external users added via access packages by specifying what happens when they lose their last access package assignment.

| Setting | Value | Reason |
| --- | --- | --- |
| Block external user from signing into this directory | Yes | When an external user loses their last assignment to any access package you should block, then remove them from the tenant. |
| Remove external user​ | Yes | When an external user loses their last assignment to any access package you should block, then remove them from the tenant. |
| Number of days before removing external user from this directory | 30 | When an external user loses their last assignment to any access package you should block, then remove them from the tenant​ |

### Password reset settings

| Setting | Value | Reason |
| --- | --- | --- |
| **Properties** |  |  |
| Self-service password reset enabled | Select users | We recommend self-service password reset for all users who can use their mobile phone for text and can install and set up the Microsoft Authenticator app. |
| **Authentication methods** |  |  |
| Number of methods required to reset | 2 | Two methods provide a balance between usability and security. |
| Methods available to users | Mobile app notification, mobile app code, email, and mobile phone \(SMS only\) | Mobile App provides the most modern and secure cryptographic methods. ​  <br>Then, email or SMS can be used as another option.  <br>We strongly recommended deploying passwordless authentication methods to accounts in EDU tenants. This improves user experience. |
| **Registration** |  |  |
| Require users to register when signing in? | Yes | With this value, accounts will be interrupted to provide registration to SSPR upon first sign-in. This helps to onboard accounts with a consistent baseline. |
| Number of days before users are asked to reconfirm their authentication information | 180 |  |
| *Notifications* |  |  |
| Notify users on password resets? | Yes | Notifications will provide visibility of this sensitive credential management operation. |
| Notify all admins when other admins reset their password? | Yes | Notifications will provide visibility of this sensitive credential management operation. |

### Security settings

| Setting | Value | Reason |
| --- | --- | --- |
| **Authentication method policy** |  |  |
| FIDO2 Security Key | Yes – Select users |  |
| Microsoft Authenticator passwordless sign in | Yes – Select users |  |
| Text message | No | Phone number must be assigned to all users who need to use this feature.  <br>If there's no strong use case for this capability, the overhead of adding the phone numbers isn't warranted. |

## Next steps

[Design an account strategy](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/design-account-strategy)
