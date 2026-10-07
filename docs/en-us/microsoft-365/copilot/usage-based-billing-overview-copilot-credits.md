<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits -->
<!-- Sitemap-Last-Modified: 2026-09-11 -->

# Understand usage-based billing and cost management for Copilot Credits

Microsoft's usage-based billing model charges customers based on actual usage, measured in Copilot Credits. This model complements fixed subscription licensing with a flexible payment option that aligns to actual usage.

Depending on the service, organizations can use fixed licensing, the Copilot Credit Pre-purchase Plan \(P3\), pay-as-you-go billing, prepaid capacity packs, or supported combinations of these billing methods. Administrators use the Cost management dashboard in the Microsoft 365 admin center to govern access, establish spending controls, manage credit requests, and monitor consumption.

Note

To learn more about how to set up, see [Set up usage-based billing for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup).

## Watch: Microsoft Copilot Cost management

Check out this and other videos on our [YouTube channel](https://go.microsoft.com/fwlink/?linkid=2198103).

<iframe src="https://learn-video.azurefd.net/vod/player?id=ca87eab0-ba09-4d17-8f27-2da6c0b513f2" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Understand Copilot Credits

Copilot Credits are a common currency for eligible Microsoft services with usage-based billing. For more information about licensing details for Copilot Credits and services, see the [Copilot Credits Guide](https://aka.ms/CopilotCredits/LicensingGuide).

## Services managed by usage-based billing

Microsoft will add more agents and services over time and provide notifications and updated content as they become available.

Services managed by usage-based billing in the Microsoft admin center now include:

Microsoft 365 Copilot

- Cowork \(Copilot license required\)
- Advanced work in SharePoint \(Copilot license required\)
- Advanced work in OneDrive \(Copilot license required\)
- Work IQ API for custom apps and agents
- Copilot Managed Runtime
- Teams Phone Agent

Spending policies can automatically apply to future supported Microsoft Copilot services and agents. The **Auto-apply new services** setting is enabled by default for spending policies. Administrators can turn off the setting for policies where future services and agents should be reviewed before they're added. For more information, see [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits#select-agents-and-services).

Important

Review existing spending policies to determine whether automatic coverage is appropriate. No action is required when you want future supported services and agents to inherit the policy.

In the Microsoft admin center, **Copilot > Cost management**, admins can monitor Copilot Credit consumption and manage spending associated with the supported services such as **Cowork**, running apps hosted on the **Copilot Managed Runtime**, and **Work IQ API**.

Building apps hosted on the Copilot Managed Runtime apps consumes Copilot Credits and follows the spending policies and credit allocations you configure in the product where you create the apps. For running apps, administrators can configure separate spending policies and credit allocations in the Microsoft 365 admin center by using the **Copilot Managed Runtime** service.

For more information, see:

- [Copilot Cowork Overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/index)
- [Work IQ API overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/api-overview)
- [Manage apps in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/managed-apps)
- [Manage Copilot Cowork for your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
- [Planning Teams Phone Agent](https://learn.microsoft.com/en-us/microsoftteams/aa-cq-plan-overview#teams-phone-agent)
- [Copilot in SharePoint](https://learn.microsoft.com/en-us/SharePoint/copilot-in-sharepoint-get-started)

Estimate Cowork usage: Use the [Copilot Credit Estimator](https://aka.ms/CopilotCreditPlanningModel) to model potential credit usage for your organization.

Note

If you're looking for information about other usage-based billing products, use the following articles:

- For Copilot Chat, SharePoint Agents, or Microsoft Copilot Retrieval API \(Preview\), see [Microsoft Copilot pay-as-you-go service overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/overview).
- For Copilot Studio, see [Copilot Studio pay-as-you-go](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing#copilot-studio-pay-as-you-go).
- For non-Copilot services such as Microsoft 365 Backup, Microsoft 365 SharePoint Storage, and High Volume Email, see [Set up and manage pay-as-you-go billing in the Billing node of the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node).

## Manage usage-based billing in the Microsoft 365 admin center

### Use the cost management dashboard

The Cost management dashboard in the Microsoft 365 admin center provides a centralized place to govern and monitor AI experiences enabled by usage-based billing.

Administrators can use the dashboard to:

- Configure spending policies.
- Control which users and groups can access supported services.
- Apply organization-level and user-level spending limits.
- Automatically apply policies to future supported services and agents.
- Configure policy alerts and user-level threshold notifications.
- Manage billing methods.
- Configure custom routing for credit requests.
- Review consumption by spending policy, user, group, agent, service, and funding source.

Supported reader-based roles can review consumption dashboards and reports without receiving permissions to change spending policies or billing configurations. This separation enables finance, operations, licensing, and governance stakeholders to review consumption information with read-only access. For more information, see [Set up usage-based billing for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup#roles-and-requirements).

Note

While Microsoft brings more agents and services to this experience, you can manage other pay-as-you-go services in **Billing** > **Pay-as-you-go**. For more information, see [Pay-as-you-go in the Billing node](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-setup-billing-node).

### Setup and configuration

You can easily set up and govern how AI experiences based on usage-based billing are enabled and controlled across your organization.

The Configuration experience gives you a centralized place to enable usage-based billing and define how spending is managed.

Use the Configuration experience to:

- Enable usage-based billing with flexible options including Copilot Credit Pre-purchase plan \(P3\), pay-as-you-go, or existing prepaid capacity packs.
- Connect an Azure subscription to support billing.
- Create spending policies that control who can consume Copilot Credits.
- Select the agents and services covered by each policy.
- Automatically apply a policy to future supported services and agents.
- Configure policy-level and user-level spending limits.
- Configure administrator alerts and user-level threshold notifications.
- Manage your Copilot Credit balance by purchasing a Copilot Credit Pre-purchase plan \(P3\) or using existing credits.
- Select the billing method for a policy.
- Configure request-routing policies for supported credit requests.

To learn more, see [Set up usage-based billing for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup).

### Monitor spending of Copilot Credits

You can get clear visibility into how and where Copilot is used, and how to optimize it.

The **Overview** tab provides a snapshot of usage and spending of Copilot Credits. Interactive cards can open details about prepaid capacity pack consumption by service and pay-as-you-go usage. The tab also shows policies and users that are approaching their limits so that administrators can take action.

The Credit requests experience helps administrators manage requests from users who need access to supported Copilot services or require a higher spending limit.

- Track overall credit consumption and remaining capacity.
- Identify emerging trends and potential risks early.
- Understand where usage is increasing across services and users.

This feature helps administrators quickly answer: "Where are we spending, and are we on track?"

The **Consumption** tab enables detailed analysis by spending policy, user, group, agent, or service.

The **Policies** view is the default view and shows policy status, scope, active users, credit usage, current spending limit, limit utilization, and billing method for the selected reporting period.

Active users are users who generated usage during the selected period, not all users who are eligible under the policy. The current spending limit reflects the policy's current configuration even when a historical reporting period is selected.

In the **Users** view, administrators can review daily credit usage and credits spent by spending policy. This detail helps explain how an individual's usage is distributed when more than one spending policy applies.

- Drill into usage by user, group, service, or agent.
- Identify high-intensity users and cost drivers.
- Analyze consumption trends and patterns over time.
- Inform policy adjustments and smarter budget allocation.

This feature allows organizations to understand, monitor, and optimize spending of Copilot Credits.

To learn more, see [Monitor Copilot Credit spending](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending).

### Next steps

- For setup and configuration guidance, see [Set up usage-based billing for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup).
- For monitoring guidance, see [Monitor Copilot Credit spending](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending).
- For more information about discovery settings for AI experiences enabled by usage-based billing, see [Discovery setting for AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/discovery-setting-ai-experiences).

## Related articles

- [Set up usage-based billing for Copilot Credits](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-setup)
- [Manage AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits)
- [Monitor Copilot Credit spending](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-monitor-spending)
- [Usage-based-billing guidance for CSPs, partner-managed customers, and MACC](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-copilot-credits-csp-partner-macc)
- [Understanding the user subscription license \(USL\) and usage-based billing \(UBB\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/user-subscription-license-usage-based-billing)
