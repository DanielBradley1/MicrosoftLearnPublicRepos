<!-- Source: https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-device-unknown-unsupported -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Block unknown or unsupported device platform

## Overview

Users are blocked from accessing company resources when the device type is unknown or unsupported.

The [device platform condition](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-conditions#device-platforms) is based on user agent strings. Conditional Access policies using this condition should be used with another policy, like one requiring device compliance or app protection policies, to mitigate the risk of user agent spoofing.

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

6. Under **Target resources** > **Resources \(formerly cloud apps\)** > **Include**, select **All resources \(formerly 'All cloud apps'\)**.
7. Under **Conditions**, select **Device platforms**

   1. Set **Configure** to **Yes**.
   2. Under **Include**, select **Any device**
   3. Under **Exclude**, select **Android**, **iOS**, **Windows**, and **macOS**.

      Note

      For this exclusion, select any platforms that your organization uses, and leave the others unselected.
   4. Select, **Done**.

8. Under **Access controls** > **Grant**, select **Block access**, then select **Select**.
9. Confirm your settings and set **Enable policy** to **Report-only**.
10. Select **Create** to enable your policy.

After confirming your settings using [policy impact or report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results), move the **Enable policy** toggle from **Report-only** to **On**.

## Related content

- [Conditional Access templates](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policy-common)
- [Use report-only mode for Conditional Access to determine the results of new policy decisions.](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only)
