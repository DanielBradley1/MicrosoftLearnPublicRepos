<!-- Source: https://learn.microsoft.com/en-us/intune/fundamentals/account-sign-up -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Sign up or sign in to Microsoft Intune

This article can help system administrators sign up for an Intune account. Before you sign up for Intune, determine if your organization already uses [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/what-is-entra). Microsoft Entra supports work or school accounts that you use with Intune and other Microsoft online services and subscriptions, like Microsoft Azure and Microsoft 365.

- To add an Intune subscription to an Entra tenant, you must use an account that is assigned an Entra ID built-in role with sufficient permissions to add Intune. The initial sign-up page identifies the applicable built-in roles, including:

  - [Billing Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#billing-administrator)
  - [Compliance Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#compliance-administrator)

- If you don't have a Microsoft Entra tenant, then a tenant is created for your organization when you **sign up** for an Intune subscription. You can also sign up for a [trial subscription](https://learn.microsoft.com/en-us/intune/fundamentals/try-overview).

Warning

You can't combine an existing work or school account after you sign up for a new account.

Important

On October 15, 2024, Microsoft began enforcement of the Azure sign-in requirement to use multifactor authentication \(MFA\). When enforced, MFA is required for all users who sign-in to Intune admin center regardless of any roles they have or don't have. The MFA requirements also apply to services that you access through the admin center, like Windows 365 Cloud PC, and to use of the Microsoft Azure portal and Microsoft Entra admin center. MFA requirements don't apply to end users who access applications, websites, or services hosted on Azure where those users don't sign-in to the admin center.

The requirement to sign-in using MFA applies to all Intune subscriptions, including free trial subscriptions. The prerequisites and process required to configure MFA depend on the MFA method you choose to use for your tenant. Shortly after MFA is enabled for a tenant, subsequent sign-in attempts require the user to complete setup for using the configured MFA solution.

To learn more about the MFA requirement, see [Planning for mandatory multifactor authentication for Azure and admin portals](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mandatory-multifactor-authentication) in the Microsoft Entra documentation.

In the Microsoft Entra planning article, you'll find guidance and resources to help you [Prepare for multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mandatory-multifactor-authentication#prepare-for-multifactor-authentication), including methods to configure MFA including but not limited to:

- Conditional Access policies
- The *MFA Wizard for Microsoft Entra ID* from the Microsoft 365 admin center
- Entra ID *security defaults*

## Role-based access controls

Securing access to your organization is a foundational security step. We recommend immediately after you sign up for Intune, plan to use the Microsoft 365 admin center to assign a user account the Entra ID built-in role [Intune Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator).

The Intune Administrator is a privileged account. The permissions this role includes are applicable only within the scope of Microsoft Intune.

In addition to configuring Intune, an Intune Administrator can use the Intune admin center to assign other user accounts to the specific Intune built-in roles that they require to complete their regular day-to-day administrative tasks. Use of lesser-privileged roles to manage daily tasks follows the principle of *least privileged* access and reduces risk.

For enhanced security, consider enabling [Multi Admin Approval](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/multi-admin-approval) for role-based access control changes. Multi Admin Approval now supports role-based access control. When this setting is on, a second administrator must approve changes to roles. These changes can include updates to role permissions, admin groups, or member group assignments. The change takes effect only after the approval. This dual authorization process helps protect your organization from unauthorized or accidental role-based access control changes. For more information, see [Use Multi Admin Approval in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/multi-admin-approval).

For more information, see [Best practices](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/best-practices) for Microsoft Entra roles, and [Role-based access control](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview) \(RBAC\) with Microsoft Intune.

## How to sign up for Intune

1. In a web browser, open the [Intune set up account page](https://go.microsoft.com/fwlink/?linkid=2019088) and solve the puzzle to confirm you're not a robot.
2. On the *Sign-in details* page, sign in or sign up to manage a new subscription of Intune.

   ![Screenshot of the Microsoft Intune Trial account sign-up web page.](https://learn.microsoft.com/en-us/intune/fundamentals/media/account-sign-up/account-sign-up-site.png)

## Post sign up considerations

After you sign up for a new subscription, you receive an email message that contains your account information at the email address that you provided during the sign-up process. This email confirms your subscription is active.

After completing the sign-up process, you're directed to the Microsoft 365 admin center to add users and assign them licenses. If you only have cloud-based accounts using your default *onmicrosoft.com* domain name, then you can go ahead and add users and assign licenses at this point. However, if you plan to use your organization's [custom domain name](https://learn.microsoft.com/en-us/intune/fundamentals/configure-custom-domain) or [synchronize user account information](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/add-users#sync-active-directory-and-add-users-to-intune) from on-premises Active Directory, then you can close that browser window.

### Microsoft Intune Onboarding benefit

Microsoft offers an Intune Onboarding benefit for eligible services. The benefit lets you work remotely with Microsoft specialists to prepare your Intune environment for use. For more information, see [Microsoft Intune Onboarding Benefit Description](https://learn.microsoft.com/en-us/microsoft-365/fasttrack/introduction).

## Sign in to Microsoft Intune

After signing up for Intune, use any device with a [supported browser](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms#intune-supported-web-browsers) to sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) to administer the service. Administration of Intune requires your account to have sufficient RBAC permissions within Intune for the tasks you want to manage. Initially, you might use an account that is assigned the Microsoft Entra ID built-in role of [Intune Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator).

The Intune Administrator is a [privileged role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) with global permissions within Microsoft Intune. With this role a user can configure Intune, add users, create groups of users, and assign the members of those groups Intune RBAC roles that provide them less privileged administrative access for daily use.

Microsoft recommends using roles with the least privilege necessary for daily administration, reducing risk if an account is compromised. To learn more about Intune built-in and custom RBAC roles and for guidance about assigning these roles to users, see [Use role-based access control with Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

### Intune Admin portal URL

Microsoft Intune admin center: `https://intune.microsoft.com`

Intune for Education: `https://intuneeducation.portal.azure.com`

### URLs for Intune services provided by Microsoft 365

Microsoft 365 Business: `https://portal.microsoft.com/adminportal`

Microsoft 365 Mobile Device Management: `https://admin.microsoft.com/adminportal/home#/MifoDevices`

## Buy Microsoft Intune

You can purchase Microsoft Intune Plan 1, Plan 2, Suite, and standalone capability licenses through any of the following:

- A Microsoft partner or reseller
- Microsoft Volume License Servicing Center \(VLSC\)
- Web direct purchase in the [Microsoft 365 admin center](https://admin.microsoft.com)

After purchase, the licenses appear in your tenant and the corresponding capability status updates to **Active**. Each capability has its own license-count requirements based on the users you target.

For information on assigning licenses, see [Assign Microsoft Intune licenses](https://learn.microsoft.com/en-us/intune/fundamentals/assign-licenses).

## Related content

- [Configure domains](https://learn.microsoft.com/en-us/intune/fundamentals/configure-custom-domain)
- [Add users](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/add-users)
- [Add groups](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/add-groups)
