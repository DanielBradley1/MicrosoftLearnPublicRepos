<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mde-planning-guide -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Get started with your Microsoft Defender for Endpoint deployment

Tip

As a companion to this article, see our [Microsoft Defender for Endpoint setup guide](https://go.microsoft.com/fwlink/p/?linkid=2268087) to review best practices and learn about essential tools such as attack surface reduction and next-generation protection. For a customized experience based on your environment, you can access the Defender for [Endpoint automated setup guide](https://go.microsoft.com/fwlink/p/?linkid=2268088) in the Microsoft 365 admin center.

Maximize available security capabilities and better protect your enterprise from cyber threats by deploying Microsoft Defender for Endpoint and onboarding your devices. Onboarding your devices enables you to identify and stop threats quickly, prioritize risks, and evolve your defenses across operating systems and network devices.

This guide provides five steps to help deploy Defender for Endpoint as your multi-platform endpoint protection solution. It helps you choose the best deployment tool, onboard devices, and configure capabilities. Each step corresponds to a separate article.

The steps to deploy Defender for Endpoint are:

[![The deployment steps](https://learn.microsoft.com/en-us/defender/media/defender-endpoint/onboard-mde.png)](https://learn.microsoft.com/en-us/defender/media/defender-endpoint/onboard-mde.png#lightbox)

1. [Step 1 - Set up Microsoft Defender for Endpoint deployment](https://learn.microsoft.com/en-us/defender-endpoint/production-deployment): This step focuses on getting your environment ready for deployment.
2. [Step 2 - Assign roles and permissions](https://learn.microsoft.com/en-us/defender-endpoint/prepare-deployment): Identify and assign roles and permissions to view and manage Defender for Endpoint.
3. [Step 3 - Identify your architecture and choose your deployment method](https://learn.microsoft.com/en-us/defender-endpoint/deployment-strategy): Identify your architecture and the deployment method that best suits your organization.
4. [Step 4 - Onboard devices](https://learn.microsoft.com/en-us/defender-endpoint/onboarding): Assess and onboard your devices to Defender for Endpoint.
5. [Step 5 - Configure capabilities](https://learn.microsoft.com/en-us/defender-endpoint/onboard-configure): You're now ready to configure Defender for Endpoint security capabilities to protect your devices.

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

## Requirements

Here's a list of prerequisites required to deploy Defender for Endpoint:

- You're a Security Administrator
- Your environment meets the [minimum requirements](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements)
- You have a full inventory of your environment. The following table provides a starting point to gather information and ensure that stakeholders understand your environment. The inventory helps identify potential dependencies and/or changes required in technologies or processes.

Important

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

| What | Description |
| --- | --- |
| Endpoint count | Total count of endpoints by operating system. |
| Server count | Total count of Servers by operating system version. |
| Management engine | Management engine name and version \(for example, System Center Configuration Manager Current Branch 1803\). |
| CDOC distribution | High level CDOC structure \(for example, Tier 1 outsourced to Contoso, Tier 2 and Tier 3 in-house distributed across Europe and Asia\). |
| Security information and event \(SIEM\) | SIEM technology in use. |

## Next step

Start your deployment with [Step 1 - Set up Microsoft Defender for Endpoint deployment](https://learn.microsoft.com/en-us/defender-endpoint/production-deployment)
