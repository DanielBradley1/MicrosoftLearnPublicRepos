<!-- Source: https://learn.microsoft.com/en-us/entra/global-secure-access/tutorial-microsoft-traffic-compliant-network -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# Tutorial: Enable the compliant network check

The compliant network check ensures users connect through the Global Secure Access service for your tenant before they access protected resources. This tenant-bound network signal lets you use location-based Conditional Access policies without maintaining egress IP address lists or routing traffic through a VPN for source IP anchoring.

In this tutorial, you learn how to:

- Recognize what the compliant network check does and why it matters.
- Create a Conditional Access policy that blocks access from anywhere except the compliant network.
- Validate that protected apps are blocked when the Global Secure Access client is disabled.

## Key concepts

Compliant network enforcement reduces the risk of token theft and replay attacks. Microsoft Entra ID performs authentication-plane enforcement when a user authenticates. If an adversary steals a session token and tries to replay it from a device that isn't connected to your organization's compliant network, Microsoft Entra ID denies the request and blocks further access.

The compliant network check is tenant-specific. If you define a policy that requires compliant network in one tenant, only users who connect through the Global Secure Access service for that tenant can satisfy the control.

The compliant network is different from IPv4, IPv6, or geographic named locations that you configure in Conditional Access. You don't need to review or maintain compliant network IP addresses or ranges.

Note

You must [enable source IP restoration](https://learn.microsoft.com/en-us/entra/global-secure-access/tutorial-microsoft-traffic-source-ip-restoration) in order to target the compliant network in Conditional Access.

## Step 1: Create the compliant network Conditional Access policy

A typical policy blocks all network locations except compliant networks. Start with a pilot group and a specific test application before you apply the policy broadly.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a Conditional Access Administrator.
2. Browse to **Entra ID** > **Conditional Access**.
3. Select **Create new policy**.
4. Enter a meaningful policy name, such as **Require compliant network - Pilot**.
5. Under **Assignments**, select **Users or workload identities**.

   1. Under **Include**, select a test user or pilot group.

6. Under **Target resources** > **Include**, select a specific test application.
7. Under **Network**:

   1. Set **Configure** to **Yes**.
   2. Under **Include**, select **Any location**.
   3. Under **Exclude**, select **All Compliant Network locations**.

8. Under **Access controls** > **Grant**, select **Block access**, and then select **Select**.
9. Confirm your settings and set **Enable policy** to **On**.
10. Select **Create**.

## Step 2: Validate the compliant network policy

1. On a pilot device with the Global Secure Access client installed and running, attempt to sign in to an app included in the Conditional Access policy configured in step 1. You should be able to sign in normally.
2. Pause the Global Secure Access client by right-clicking the application in the Windows system tray and selecting **Disable**.
3. Open a new browser session and try to sign in again.
4. Confirm that Microsoft Entra ID blocks access.

   [![Screenshot that shows a Microsoft sign-in error stating that the user can't access the resource right now.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/tutorial-microsoft-traffic/compliant-network-block.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/tutorial-microsoft-traffic/compliant-network-block.png#lightbox)
5. Re-enable the Global Secure Access client and confirm that access is restored.

If you're already signed in to an application, access isn't interrupted immediately. Microsoft Entra ID reevaluates the compliant network check the next time sign-in is required, such as when the application session expires. Use a fresh browser session or sign out first when you validate.

## What you learned

In this exercise, you accomplished the following tasks:

- **Confirmed Conditional Access signaling:** You verified that Microsoft Entra ID can evaluate the compliant network signal.
- **Created a compliant network Conditional Access policy:** Your pilot users must connect through Global Secure Access before they can reach apps integrated with Microsoft Entra ID.
- **Validated enforcement:** You confirmed that access succeeds with the Global Secure Access client running and is blocked when the client is disabled.

## Next step

[Configure universal tenant restrictions](https://learn.microsoft.com/en-us/entra/global-secure-access/tutorial-microsoft-traffic-tenant-restrictions)
