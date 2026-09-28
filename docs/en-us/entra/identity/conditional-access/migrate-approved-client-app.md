<!-- Source: https://learn.microsoft.com/en-us/entra/identity/conditional-access/migrate-approved-client-app -->
<!-- Sitemap-Last-Modified: 2026-05-30 -->

# Migrate approved client app to application protection policy in Conditional Access

## Overview

In this article, you learn how to migrate from the "Require approved client app" Conditional Access grant control to the "Require app protection policy" grant control. App protection policies provide the same data loss and protection as approved client app policies, but with other benefits. For more information about the benefits of using app protection policies, see the article [App protection policies overview](https://learn.microsoft.com/en-us/mem/intune/apps/app-protection-policy).

The **Require approved client app** grant retirement date is extended from March 2026 to June 30, 2026. Organizations must transition all current Conditional Access policies that use **only** the **Require approved client app** grant to **Require approved client app** **or** **Require app protection policy** by June 2026. Additionally, for any new Conditional Access policy, **only** apply the **Require app protection policy** grant.

Important

On **June 30, 2026**, the Conditional Access **Require approved client app** control in Microsoft Entra and any Conditional Access policies that include the approved client app grant control move to a read-only state. Admins can no longer create new policies or edit existing ones that use this control. Admins can still disable or delete existing policies. Existing policies continue to be enforced for end users as long as they remain enabled.

## Edit an existing Conditional Access policy

Require approved client apps or app protection policy with mobile devices

The following steps make an existing Conditional Access policy require an approved client app or an app protection policy when using an iOS/iPadOS or Android device. This policy works in tandem with an app protection policy created in Microsoft Intune.

Organizations can choose to update their policies using the following steps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**.
3. Select a policy that uses the approved client app grant.
4. Under **Access controls** > **Grant**, select **Grant access**.

   1. Select **Require approved client app** and **Require app protection policy**.
   2. Under **For multiple controls**, select **Require one of the selected controls**.

5. Confirm your settings and set **Enable policy** to **Report-only**.
6. Select **Create** to enable your policy.

After confirming your settings using [policy impact or report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results), move the **Enable policy** toggle from **Report-only** to **On**.

Repeat the previous steps on all of your policies that use the approved client app grant.

Warning

Not all applications that are supported as approved applications support application protection policies. For a list of some common client apps, see [App protection policy requirement](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-grant#require-app-protection-policy). If your application isn't listed there, contact the application developer.

## Create a Conditional Access policy

Require app protection policy with mobile devices

The following steps help create a Conditional Access policy requiring an approved client app or an app protection policy when using an iOS/iPadOS or Android device. This policy works in tandem with an [app protection policy created in Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/apps/app-protection-policies).

Organizations can choose to deploy this policy using the following steps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**.
3. Select **New policy**.
4. Give your policy a name. Create a meaningful standard for the names of your policies.
5. Under **Assignments**, select **Users or workload identities**.

   1. Under **Include**, select **All users**.
   2. Under **Exclude**, select **Users and groups** and exclude at least one account to prevent yourself from being locked out. If you don't exclude any accounts, you can't create the policy.

6. Under **Target resources** > **Resources \(formerly cloud apps\)** > **Include**, select **All resources \(formerly 'All cloud apps'\)**.
7. Under **Conditions** > **Device platforms**, set **Configure** to **Yes**.

   1. Under **Include**, **Select device platforms**.
   2. Choose **Android** and **iOS**.
   3. Select **Done**.

8. Under **Access controls** > **Grant**, select **Grant access**.

   1. Select **Require approved client app** and **Require app protection policy**.

      1. Under **For multiple controls**, select **Require one of the selected controls**.

9. Confirm your settings and set **Enable policy** to **Report-only**.
10. Select **Create** to enable your policy.

After confirming your settings using [policy impact or report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results), move the **Enable policy** toggle from **Report-only** to **On**.

Note

If an app doesn't support **Require app protection policy**, end users trying to access resources from that app are blocked.

## Next steps

For more information on application protection policies, see:

[Create and assign app protection policies](https://learn.microsoft.com/en-us/intune/intune-service/apps/app-protection-policies)
