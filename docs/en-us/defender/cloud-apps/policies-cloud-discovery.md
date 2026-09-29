<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/policies-cloud-discovery -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Create cloud discovery policies in Defender for Cloud Apps

This article provides an overview of how to get started using Defender for Cloud Apps to gain visibility across your organization into Shadow IT using cloud discovery.

Defender for Cloud Apps enables you to discover and analyze cloud apps that are in use in your organization's environment. The cloud discovery dashboard shows all the cloud apps running in the environment and categorizes them by function and enterprise readiness. For each app, discover the associated users, IP addresses, devices, transactions, and conducts risk assessment without needing to install an agent on your endpoint devices.

## Detect new high-volume or wide app use 

Detect new apps that are highly used, in terms of number of users or amount of traffic in your organization.

### Prerequisites

Configure automatic log upload for continuous cloud discovery reports, as described in [Configure automatic log upload for continuous reports](https://learn.microsoft.com/en-us/defender-cloud-apps/discovery-docker) or enable the Defender for Cloud Apps integration with Defender for Endpoint, as described in [Integrate Microsoft Defender for Endpoint with Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/mde-integration).

### Create a high-volume app discovery policy

Perform the following steps to create a policy for detecting new high-volume or popular apps.

1. In the Microsoft Defender Portal, under **Cloud Apps**, go to **Policies** -> **Policy management**. Create a new **App discovery policy**.
2. In the **Policy template** field, select **New high volume app** or **New popular app** and apply the template.
3. Customize policy filters to meet your organization's requirements.
4. Configure the actions to be taken when an alert is triggered.

Note

An alert is generated once for each new app that wasn't discovered in the last 90 days.

## Detect new risky or non-compliant app use

Detect potential exposure of your organization in cloud apps that don't meet your security standards.

### Prerequisites

Configure automatic log upload for continuous cloud discovery reports, as described in [Configure automatic log upload for continuous reports](https://learn.microsoft.com/en-us/defender-cloud-apps/discovery-docker) or enable the Defender for Cloud Apps integration with Defender for Endpoint, as described in [Integrate Microsoft Defender for Endpoint with Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/mde-integration).

### Create a risky app discovery policy

Perform the following steps to create a policy that detects risky or non-compliant app use.

1. In the Microsoft Defender Portal, under **Cloud Apps**, go to **Policies** -> **Policy management**. Create a new **App discovery policy**.
2. In the **Policy template** field, select the **New risky app** template and apply the template.
3. Under **App matching all of the following** set the [Risk Score](https://learn.microsoft.com/en-us/defender-cloud-apps/risk-score) slider and the Compliance risk factor to customize the level of risk you want to trigger an alert, and set the other policy filters to meet your organization's security requirements.

   1. Optional: To get more meaningful detections, customize the amount of traffic that will trigger an alert.
   2. Check the **Trigger a policy match if all the following occur on the same day** checkbox.
   3. Select **Daily traffic** greater than 2,000 GB \(or other\).

4. Configure governance actions to be taken when an alert is triggered. Under **Governance**, select **Tag app as unsanctioned.**

   Important

   Selecting **Tag app as unsanctioned** automatically blocks access to the app when the policy is matched.
5. Optional: Apply [Defender for Cloud Apps native integrations](https://learn.microsoft.com/en-us/defender-cloud-apps/set-up-cloud-discovery) with Secure Web Gateways to block app access.

## Detect use of unsanctioned business apps

You can detect when your employees continue to use unsanctioned apps as a replacement for approved business-ready apps.

### Prerequisites

- Configure automatic log upload for continuous cloud discovery reports, as described in [Configure automatic log upload for continuous reports](https://learn.microsoft.com/en-us/defender-cloud-apps/discovery-docker) or enable the Defender for Cloud Apps integration with Defender for Endpoint, as described in [Integrate Microsoft Defender for Endpoint with Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/mde-integration).

### Create an unsanctioned app discovery policy

App tags are labels you assign to discovered apps so you can filter and target them in discovery policies. Perform the following steps to detect use of unsanctioned business apps.

1. In the Cloud app catalog, search for your business-ready apps and mark them with a [custom app tag](https://learn.microsoft.com/en-us/defender-cloud-apps/discovered-app-queries#creating-and-managing-custom-app-tags).
2. Follow the steps in [Detect new high volume or wide app usage](#detect-volume).
3. Add an **App tag** filter and choose the app tags you created for your business-ready apps.
4. Configure governance actions to be taken when an alert is triggered. Under **Governance**, select **Tag app as unsanctioned**.

   Important

   Selecting **Tag app as unsanctioned** automatically blocks access to the app when the policy is matched.
5. Optional: Use [Defender for Cloud Apps native integrations](https://learn.microsoft.com/en-us/defender-cloud-apps/set-up-cloud-discovery) with Secure Web Gateways to block app access.

## Detect risky OAuth apps

Get visibility and control over [OAuth apps](https://learn.microsoft.com/en-us/defender-cloud-apps/investigate-risky-oauth) that are installed inside apps like Google Workspace, Microsoft 365, and Salesforce. OAuth apps that request high permissions and have rare community use might be considered risky.

### Prerequisites

You must have the Google Workspace, Microsoft 365, or Salesforce app connected using [app connectors](https://learn.microsoft.com/en-us/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps).

### Create a risky OAuth app policy

Perform the following steps to create a policy for detecting risky OAuth apps.

1. In the Microsoft Defender Portal, under **Cloud Apps**, go to **Policies** -> **Policy management**. Create a new **OAuth app policy**.
2. Select the filter **App** and set the app the policy should cover, Google Workspace, Microsoft 365, or Salesforce.
3. Select **Permission level** filter equals **High** \(available for Google Workspace and Microsoft 365\).
4. Add the filter **Community use** equals **Rare**.
5. Configure the actions to take when an alert is triggered. For example, for Microsoft 365, check **Revoke app** for OAuth apps detected by the policy.

Note

Supported for Google Workspace, Microsoft 365, and Salesforce app stores.

## Related content

[Best practices for protecting your organization](https://learn.microsoft.com/en-us/defender-cloud-apps/best-practices)
