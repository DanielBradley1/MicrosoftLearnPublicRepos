<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b -->
<!-- Sitemap-Last-Modified: 2026-04-25 -->

# What is Microsoft Entra B2B collaboration?

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Microsoft Entra External ID includes collaboration capabilities that allow your workforce to work securely with business partners and guests. In your workforce tenant, you can use B2B collaboration to share your company's applications and services with guests, while maintaining control over your own corporate data. Work securely with external partners, even if they don't have Microsoft Entra ID or an IT department.

![Diagram illustrating B2B collaboration.](https://learn.microsoft.com/en-us/entra/external-id/media/what-is-b2b/b2b-collaboration-overview.png)

A simple invitation and redemption process lets partners use their own credentials to access your company's resources. You can also enable self-service sign-up user flows to let guests sign up for apps or resources themselves. Once the guest redeems their invitation or completes sign-up, they're represented in your directory as a user object. The user type for these B2B collaboration users is typically set to "guest" and their user principal name contains the #EXT# identifier.

Developers can use Microsoft Entra business-to-business APIs to customize the invitation process or write applications like self-service sign-up portals. For licensing and pricing information related to guest users, refer to [Billing model for Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/external-identities-pricing).

Important

The [email one-time passcode](https://learn.microsoft.com/en-us/entra/external-id/one-time-passcode) feature is now turned on by default for all new tenants and for any existing tenants where you haven't explicitly turned it off. When this feature is turned off, the fallback authentication method is to prompt invitees to create a Microsoft account.

## Collaborate with any partner using their identities

With Microsoft Entra B2B, the partner uses their own identity management solution, so there's no external administrative overhead for your organization. Guest users sign in to your apps and services with their own work, school, or social identities.

- The partner uses their own identities and credentials, whether or not they have a Microsoft Entra account.
- You don't need to manage external accounts or passwords.
- You don't need to sync accounts or manage account lifecycles.

## Manage B2B collaboration with other organizations

B2B collaboration is enabled by default, but comprehensive admin settings let you control your inbound and outbound B2B collaboration with external partners and organizations.

- **Cross-tenant access settings.** For B2B collaboration with other Microsoft Entra organizations, use [cross-tenant access settings](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-overview) to control which users can authenticate with which resources. Manage inbound and outbound B2B collaboration, and scope access to specific users, groups, and applications. Set a default configuration that applies to all external organizations, and then create individual, organization-specific settings as needed. Using cross-tenant access settings, you can also trust multifactor \(MFA\) and device claims \(compliant claims and Microsoft Entra hybrid joined claims\) from other Microsoft Entra organizations.
- **External collaboration settings.** Use [external collaboration settings](https://learn.microsoft.com/en-us/entra/external-id/external-collaboration-settings-configure) to define who can invite external users into your organization as guests. By default, all users in your organization, including B2B collaboration guest users, can invite external users to B2B collaboration. If you want to limit the ability to send invitations, you can turn invitations on or off for everyone, or limit invitations to certain roles. You can also allow or block B2B specific domains and set restrictions on guest user access to your directory.

These settings are used to manage two different aspects of B2B collaboration. Cross-tenant access settings control whether users can authenticate with external Microsoft Entra tenants. They apply to both inbound and outbound B2B collaboration. By contrast, external collaboration settings control which users in your organization are allowed to send B2B collaboration invitations to guests from any organization.

### How cross-tenant access and external collaboration settings work together

When you're considering B2B collaboration with a specific external Microsoft Entra organization, determine whether your cross-tenant access settings allow B2B collaboration with that organization. Also consider whether your external collaboration settings allow your users to send invitations to that organization's domain. Here are some examples:

- **Example 1**: You previously added `adatum.com` \(a Microsoft Entra organization\) to the list of blocked domains in your external collaboration settings, but your cross-tenant access settings enable B2B collaboration for all Microsoft Entra organizations. In this case, the most restrictive setting applies. Your external collaboration settings prevent your users from sending invitations to users at `adatum.com`.
- **Example 2**: You allow B2B collaboration with Fabrikam in your cross-tenant access settings, but then you add `fabrikam.com` to your blocked domains in your external collaboration settings. Your users can't invite new Fabrikam business guests, but existing Fabrikam guests can continue using B2B collaboration.

Note

Microsoft began rolling out an update to the guest user sign-in experience for B2B collaboration in July 2025, and the rollout completed by the end of 2025. With this update, guest users are redirected to their own organization's sign-in page to provide credentials. Guest users see the branding and URL endpoint of their home tenant. Following successful authentication in their own organization, guest users are returned to your organization to complete sign-in.

### Manage B2B collaboration with other Microsoft clouds

Microsoft Azure cloud services are available in separate national clouds, which are physically isolated instances of Azure. Increasingly, organizations are finding the need to collaborate with organizations and users across global cloud and national cloud boundaries. With Microsoft cloud settings, you can establish mutual B2B collaboration between the following Microsoft Azure clouds:

- Microsoft Azure global cloud and [Microsoft Azure Government](https://learn.microsoft.com/en-us/azure/azure-government/)
- Microsoft Azure global cloud and [Microsoft Azure operated by 21Vianet](https://learn.microsoft.com/en-us/azure/china/)

To set up B2B collaboration between tenants in different clouds, both tenants configure their Microsoft cloud settings to enable collaboration with the other cloud. Then each tenant configures inbound and outbound cross-tenant access with the tenant in the other cloud. See [Microsoft cloud settings](https://learn.microsoft.com/en-us/entra/external-id/cross-cloud-settings) for details.

## Easily invite guest users from the Microsoft Entra admin center

As an administrator, you can easily add guest users to your organization in the admin center.

- [Create a new guest user](https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-add-guest-users-portal) in Microsoft Entra ID, similar to how you'd add a new user.
- Assign guest users to apps or groups.
- [Send an invitation email](https://learn.microsoft.com/en-us/entra/external-id/invitation-email-elements) that contains a redemption link, or send a direct link to an app you want to share.

[![Screenshot showing the Invite a new guest user invitation entry page.](https://learn.microsoft.com/en-us/entra/external-id/media/what-is-b2b/add-a-b2b-user.png)](https://learn.microsoft.com/en-us/entra/external-id/media/what-is-b2b/add-a-b2b-user.png#lightbox)

- Guest users follow a few simple redemption steps to sign in.

![Screenshot showing the Review permissions page.](https://learn.microsoft.com/en-us/entra/external-id/media/what-is-b2b/consent-screen.png)

## Allow self-service sign-up

With a self-service sign-up user flow, you can create a sign-up experience for guests who want to access your apps. As part of the sign-up flow, you can provide options for different social or enterprise identity providers, and collect information about the user. Learn about [self-service sign-up and how to set it up](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-overview).

You can also use API connectors to integrate your self-service sign-up user flows with external cloud systems. You can connect with custom approval workflows, perform identity verification, validate user-provided information, and more.

![Screenshot showing the user flows page.](https://learn.microsoft.com/en-us/entra/external-id/media/what-is-b2b/self-service-sign-up-user-flow-overview.png)

## Use policies to securely share your apps and services

You can use authentication and authorization policies to protect your corporate content. Conditional Access policies, such as multifactor authentication, can be enforced:

- At the tenant level
- At the application level
- For specific guest users to protect corporate apps and data

![Screenshot showing the Conditional Access option.](https://learn.microsoft.com/en-us/entra/external-id/media/what-is-b2b/tutorial-mfa-policy-2.png)

## Let application and group owners manage their own guest users

You can delegate guest user management to application owners. This allows them to add guest users directly to any application they want to share, whether it's a Microsoft application or not.

- Administrators set up self-service app and group management.
- Nonadministrators use their [Access Panel](https://myapps.microsoft.com) to add guest users to applications or groups.

[![Screenshot showing the Access panel for a guest user.](https://learn.microsoft.com/en-us/entra/external-id/media/what-is-b2b/access-panel-manage-app.png)](https://learn.microsoft.com/en-us/entra/external-id/media/what-is-b2b/access-panel-manage-app.png#lightbox)

## Customize the onboarding experience for B2B guest users

Bring your external partners on board in ways customized to your organization's needs.

- Use [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-overview) to configure policies that [manage access for external users](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-external-users#how-access-works-for-external-users).
- Use the [B2B collaboration invitation APIs](https://learn.microsoft.com/en-us/graph/api/resources/invitation) to customize your onboarding experiences.

## Integrate with identity providers

Microsoft Entra External ID supports external identity providers like Facebook, Microsoft accounts, Google, or enterprise identity providers. You can set up federation with identity providers. This way your guests can sign in with their existing social or enterprise accounts instead of creating a new account just for your application. Learn more about [identity providers for External ID](https://learn.microsoft.com/en-us/entra/external-id/identity-providers).

![Screenshot showing the Identity providers page.](https://learn.microsoft.com/en-us/entra/external-id/media/what-is-b2b/identity-providers.png)

## Integrate with SharePoint and OneDrive

You can [enable integration with SharePoint and OneDrive](https://learn.microsoft.com/en-us/sharepoint/sharepoint-azureb2b-integration) to share files, folders, list items, document libraries, and sites with people outside your organization, while using Microsoft Entra B2B for authentication and management. The users you share resources with are typically guest users in your directory, and permissions and groups work the same for these guests as they do for internal users. When enabling integration with SharePoint and OneDrive, you also enable the [email one-time passcode](https://learn.microsoft.com/en-us/entra/external-id/one-time-passcode) feature in Microsoft Entra B2B to serve as a fallback authentication method.

![Screenshot of the email one-time-passcode setting.](https://learn.microsoft.com/en-us/entra/external-id/media/what-is-b2b/enable-email-otp-options.png)

## Related content

- [Add B2B collaboration guest users in the admin center](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator)
- [B2B direct connect](https://learn.microsoft.com/en-us/entra/external-id/b2b-direct-connect-overview)
