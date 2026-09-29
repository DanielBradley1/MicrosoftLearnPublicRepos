<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/production-deployment -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Prepare to deploy Microsoft Defender for Endpoint

The first step when deploying Microsoft Defender for Endpoint is to set up your Defender for Endpoint environment.

In this Microsoft Defender for Endpoint deployment guide, you're guided through the steps on:

- Licensing validation
- Tenant configuration
- Network configuration

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

This Defender for Endpoint deployment guide covers only deployments that use Microsoft Configuration Manager. Defender for Endpoint supports the use of other onboarding tools but this deployment guide doesn't cover those onboarding-tool scenarios. For more information, see [Identify Defender for Endpoint architecture and deployment method](https://learn.microsoft.com/en-us/defender-endpoint/deployment-strategy).

Tip

As a companion to this article, see our [Microsoft Defender for Endpoint setup guide](https://go.microsoft.com/fwlink/p/?linkid=2268087) to review best practices and learn about essential tools such as attack surface reduction and next-generation protection. For a customized experience based on your environment, you can access the Defender for [Endpoint automated setup guide](https://go.microsoft.com/fwlink/p/?linkid=2268088) in the Microsoft 365 admin center.

## Check your license state

Checking the license state and whether the license was properly provisioned can be done through the Microsoft 365 admin center or through the **Microsoft Azure portal**.

- In the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/), in the navigation pane, expand **Billing**, and then select **Your products**.
- In the [Microsoft Azure portal](https://portal.azure.com/#home), under **Manage Microsoft Entra ID**, select **View**. Then, under **Manage**, select **Licenses**.

## Validate your Cloud Solution Provider setup

If you're a Cloud Service Provider \(CSP\) partner managing a customer tenant, you can check which licenses are provisioned and verify their state through the Microsoft 365 admin center.

1. From the **Partner portal**, select **Administer services** > **Office 365**.
2. Selecting the **Partner portal** link opens the **Admin on behalf** option and gives you access to the customer admin center.

   [![The Office 365 admin portal](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-o365-admin-portal-customer.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-o365-admin-portal-customer.png#lightbox)

## Configure your tenant settings

To provision Defender for Endpoint in your tenant, follow these steps:

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, select any of the following items:

   - Under **Assets**, select **Devices**.
   - Under **Endpoints**, select an item, such as **Dashboard** or **Endpoint security policies**.

## Review data center location requirements

Microsoft Defender for Endpoint stores and process data in the [same location as used by Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable). If Microsoft Defender XDR hasn't been turned on yet, onboarding to Defender for Endpoint also turns on Defender XDR, and a new data center location is automatically selected based on the location of active Microsoft 365 security services. The selected data center location is shown in the Microsoft Defender portal.

## Configure network access for deployment

Ensure devices can connect to the Defender for Endpoint cloud services. The use of a proxy is recommended. See the following articles to configure your network:

1. [Configure your network environment to ensure connectivity with Defender for Endpoint service](https://learn.microsoft.com/en-us/defender-endpoint/configure-environment).
2. [Configure your devices to connect to the Defender for Endpoint service using a proxy](https://learn.microsoft.com/en-us/defender-endpoint/configure-proxy-internet).
3. [Verify client connectivity to Microsoft Defender for Endpoint service URLs](https://learn.microsoft.com/en-us/defender-endpoint/verify-connectivity).

In environments that restrict outbound URL-based filtering, you might want to allow traffic to specific IP addresses. Not all services are accessible through specific IP addresses, and you need to evaluate how to address this potential issue in your environment. For example, you might need to download updates to a central location and then distribute them. For more information, see [Configure connectivity using static IP ranges](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-connectivity#option-2-configure-connectivity-using-static-ip-ranges).

## Next steps

After you complete the environment setup described in this guide, proceed to assign the required roles and permissions:

[Step 2 - Assign roles and permissions](https://learn.microsoft.com/en-us/defender-endpoint/prepare-deployment)
