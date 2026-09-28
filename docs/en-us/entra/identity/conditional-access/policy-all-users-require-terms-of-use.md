<!-- Source: https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-require-terms-of-use -->
<!-- Sitemap-Last-Modified: 2026-04-07 -->

# Require terms of use to be accepted before accessing Microsoft Admin Portals

## Overview

Organizations might want to require users to accept [terms of use \(ToU\)](https://learn.microsoft.com/en-us/entra/identity/conditional-access/terms-of-use) before accessing certain applications in their environment. This example helps you create a policy requiring terms of use to be accepted as part of the initial sign in process for administrators who access any of the [Microsoft Admin Portals](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps#microsoft-admin-portals).

## Create your terms of use

This section provides you with the steps to create a sample terms of use document. When you create a terms of use document, you select a value for **Enforce with Conditional Access policy templates**. Selecting **Custom policy** opens a dialog to create a new Conditional Access policy as soon as your terms of use is created.

1. Create a new terms of use document and save it as a PDF file.
2. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
3. Browse to **Entra ID** > **Conditional Access** > **Terms of use**.
4. In the menu on the top, select **New terms**.
5. In the **Name** textbox, provide a name for your terms of use policy.
6. Upload your terms of use PDF file.

   1. Select your default language.
   2. In the **Display name** textbox, type the name you want to be displayed.

7. For **Require users to expand the terms of use**, select **On**.
8. For **Enforce with Conditional Access policy templates**, select **Custom policy**.
9. Select **Create**.

## Create a Conditional Access policy

This section shows how to create the required Conditional Access policy.

**To configure your Conditional Access policy:**

1. Give your policy a name. Create a meaningful standard for the names of your policies.
2. Under **Assignments**, select **Users or workload identities**.

   1. Under **Include**, select **All users**.
   2. Under **Exclude**, select **Users and groups** and choose your organization's emergency access or break-glass accounts.

3. Under **Target resources** > **Resources \(formerly cloud apps\)**, select the following options:

   1. Under **Include**, choose **Select resources**.
   2. Select **Microsoft Admin Portals**, and then choose **Select**.

4. Under **Access controls**, select **Grant**.

   1. Select **Grant access**.
   2. Select the terms of use you created previously and choose **Select**.

5. Confirm your settings and set **Enable policy** to **Report-only**.
6. Select **Create** to enable your policy.

After confirming your settings using [policy impact or report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results), move the **Enable policy** toggle from **Report-only** to **On**.

## Test your Conditional Access policy

In the previous section, you created a Conditional Access policy requiring terms of use be accepted when accessing any of the [Microsoft Admin Portals](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps#microsoft-admin-portals).

To test your policy, try to sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) using a test account. You should see a dialog that requires you to accept your terms of use.

## User exclusions

Conditional Access policies are powerful tools. We recommend excluding the following accounts from your policies:

- **Emergency access** or **break-glass** accounts to prevent lockout due to policy misconfiguration. In the unlikely scenario where all administrators are locked out, your emergency access administrative account can be used to sign in and recover access.

  - More information can be found in the article, [Manage emergency access accounts in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access).

- **Service accounts** and **Service principals**, such as the Microsoft Entra Connect Sync Account. Service accounts are noninteractive accounts that aren't tied to any specific user. They're typically used by backend services to allow programmatic access to applications, but they're also used to sign in to systems for administrative purposes. Calls made by service principals aren't blocked by Conditional Access policies scoped to users. Use Conditional Access for workload identities to define policies that target service principals.

  - If your organization uses these accounts in scripts or code, replace them with [managed identities](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).

## Related content

[Microsoft Entra terms of use](https://learn.microsoft.com/en-us/entra/identity/conditional-access/terms-of-use)

[Conditional Access templates](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policy-common)

[Use report-only mode for Conditional Access to determine the results of new policy decisions.](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only)
