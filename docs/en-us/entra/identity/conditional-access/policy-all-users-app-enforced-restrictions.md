<!-- Source: https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-app-enforced-restrictions -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Use application enforced restrictions for unmanaged devices

## Overview

This policy can help organizations accomplish the following initiatives:

- [Block or limit access to a specific SharePoint site or OneDrive](https://learn.microsoft.com/en-us/sharepoint/control-access-from-unmanaged-devices#block-or-limit-access-to-a-specific-sharepoint-site-or-onedrive)
- [Limit access to email attachments in Outlook on the web and the new Outlook for Windows](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-identity-device-access-policies-exchange#limit-access-to-exchange-online-from-outlook-on-the-web)
- [Enforce idle session timeout on unmanaged devices](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/idle-session-timeout-web-apps#idle-session-timeout-on-unmanaged-devices)

## User exclusions

Conditional Access policies are powerful tools. We recommend excluding the following accounts from your policies:

- **Emergency access** or **break-glass** accounts to prevent lockout due to policy misconfiguration. In the unlikely scenario where all administrators are locked out, your emergency access administrative account can be used to sign in and recover access.

  - More information can be found in the article, [Manage emergency access accounts in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access).

- **Service accounts** and **Service principals**, such as the Microsoft Entra Connect Sync Account. Service accounts are noninteractive accounts that aren't tied to any specific user. They're typically used by backend services to allow programmatic access to applications, but they're also used to sign in to systems for administrative purposes. Calls made by service principals aren't blocked by Conditional Access policies scoped to users. Use Conditional Access for workload identities to define policies that target service principals.

  - If your organization uses these accounts in scripts or code, replace them with [managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).

## Template deployment

Organizations can deploy this policy by following the steps outlined below or by using the [Conditional Access templates](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policy-common).

## Create a Conditional Access policy

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**.
3. Select **New policy**.
4. Give your policy a name. Create a meaningful standard for the names of your policies.
5. Under **Assignments**, select **Users or workload identities**.

   1. Under **Include**, select **All users**
   2. Under **Exclude**, select **Users and groups** and choose your organization's emergency access or break-glass accounts.

6. Under **Target resources** > **Resources \(formerly cloud apps\)**, select the following options:

   1. Under **Include**, choose **Select resources**.
   2. Choose **Office 365**, then select **Select**.

7. Under **Access controls** > **Session**, select **Use app enforced restrictions**, then select **Select**.
8. Confirm your settings and set **Enable policy** to **Report-only**.
9. Select **Create** to enable your policy.

After confirming your settings using [policy impact or report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results), move the **Enable policy** toggle from **Report-only** to **On**.

## Related content

[Conditional Access templates](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policy-common)

[Use report-only mode for Conditional Access to determine the results of new policy decisions.](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only)
