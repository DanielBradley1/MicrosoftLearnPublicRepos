<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/optimize-copilot-configuration-settings -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# Optimize Microsoft Copilot configuration settings

Note

**The Microsoft 365 Copilot app is now called Microsoft Copilot**. The primary URL for accessing the updated Copilot app is changing to `copilot.cloud.microsoft`. To help ensure users' connections aren't blocked, make sure to:

- Allow `*.cloud.microsoft`.
- Allow the Microsoft Copilot endpoints.
- Verify that proxies, firewalls, Conditional Access, tenant restrictions, and app-control policies don't block the Copilot app.
- Do not block `copilot.cloud.microsoft` to prevent personal account access. Instead, use [tenant restrictions](https://learn.microsoft.com/en-us/entra/external-id/tenant-restrictions-v2#step-2-block-consumer-account-or-microsoft-account-tenants) to control personal Microsoft-account sign.

For more information, see [Network requirements for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements#network-requirements).

Microsoft Copilot includes settings and configuration options that can help organizations optimize Copilot availability, adoption, and usage. This article describes key configuration areas to review as you deploy and manage Copilot.

**The configurations described in this article aren't intended as universal recommendations to enable every capability.** Your organization's requirements can vary, based on factors such as your:

- Microsoft 365 environment
- Cloud environment
- Licensing
- Security and compliance requirements
- Deployment strategy

Review each configuration and determine the appropriate setting for your organization.

Important

**Government and regulated environments:** Feature availability and appropriate configurations can vary by cloud environment and organizational requirements. Before enabling a capability, verify that it's available in your environment and evaluate the configuration against your organization's security, compliance, data handling, and regulatory requirements.

## Why reviewing your configuration matters

Microsoft Copilot relies on settings and services across Microsoft 365. Reviewing your Copilot configuration can help make sure users have access to the Copilot capabilities your organization intends to make available and that those experiences align with your organization's requirements.

Because Copilot capabilities continue to evolve, periodically review your configuration and evaluate new capabilities before making them broadly available.

## Copilot configuration areas

Consider the following configuration areas when you deploy and manage Microsoft Copilot.

- [Microsoft Frontier program](#microsoft-frontier-program)
- [Usage-based billing](#usage-based-billing)
- [Microsoft 365 Apps channel readiness](#microsoft-365-apps-channel-readiness)
- [Web search](#web-search)
- [Microsoft Copilot app pinned to the Windows taskbar](#microsoft-copilot-app-pinned-to-the-windows-taskbar)
- [Teams meeting transcription](#teams-meeting-transcription)
- [Copilot Analytics](#copilot-analytics)
- [Microsoft 365 feedback and logs](#microsoft-365-feedback-and-logs)
- [AI providers operating as Microsoft subprocessors](#ai-providers-operating-as-microsoft-subprocessors)
- [Copilot connectors](#copilot-connectors)
- [Agent access and deployment](#agent-access-and-deployment)

The appropriate configuration depends on your organization's requirements, policies, licensing, cloud environment, and deployment strategy.

### Microsoft Frontier program

The Microsoft Frontier program provides eligible organizations preview access to innovative and emerging capabilities in Microsoft 365 before those features reach general availability \(GA\).

Review the program and determine whether participation is appropriate for your organization and which users should have access to eligible capabilities.

**Why review this configuration:**

- Depending on applicable licensing and other controls, you can determine which users can access eligible Frontier preview capabilities, including Copilot capabilities, before general availability.
- Allows organizations to evaluate upcoming capabilities.

For more information, see [Get started with the Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier).

### Usage-based billing

Some Microsoft Copilot and agent experiences use usage-based billing. When AI experiences enabled by usage-based billing are available to your organization, applicable experiences can consume Copilot Credits.

Review usage-based billing and determine which applicable experiences should be available in your organization.

**Why review this configuration:**

- Determines the availability of applicable AI experiences that use consumption-based billing.
- Helps your organization manage Copilot Credit consumption.
- Allows administrators to apply cost-management controls appropriate for your organization.

For more information, see [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits).

### Microsoft 365 Apps channel readiness

Keep Microsoft 365 Apps on an update channel and build that supports the Copilot capabilities you deploy.

Review the update channels used in your organization and make sure Copilot-licensed devices receive supported Microsoft 365 Apps updates.

**Why review this configuration:**

- Helps make supported Copilot capabilities available to users.
- Helps devices receive applicable Copilot features, updates, and fixes.
- Allows administrators to manage how Microsoft 365 Apps updates are deployed across their organization.

For more information, see [Change update channel of Microsoft 365 Apps to enable Copilot](https://learn.microsoft.com/en-us/microsoft-365-apps/updates/change-channel-for-copilot).

### Web search

By using web search, Microsoft Copilot can retrieve current public information from the web. Copilot can generate search queries based on a user's prompt and use relevant web results to supplement its response.

Review the web search configuration and decide whether to make web search available to users in your organization.

**Why review this configuration:**

- Determines whether Copilot can use current public information from the web.
- Affects the sources of information available to Copilot when generating responses.
- Gives administrators control over the availability of web search in their organization.

For more information, see [Data, privacy, and security for web search in Microsoft Copilot and Microsoft Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-public-web-access).

### Microsoft Copilot app pinned to the Windows taskbar

You can pin the Microsoft Copilot app to the Windows taskbar to provide users with an entry point to Copilot from their Windows devices.

Review your organization's application deployment strategy and decide whether to pin the Microsoft Copilot app to the taskbar for your users.

**Why review this configuration:**

- Determines how prominently Copilot is presented on managed Windows devices.
- Can make Copilot easier for users to find and access.
- Allows organizations to manage the Copilot entry point across devices.

For more information, see [Pin Microsoft Copilot and its companion apps to the Windows taskbar](https://learn.microsoft.com/en-us/microsoft-365/copilot/pin-copilot-taskbar).

### Teams meeting transcription

Microsoft Copilot in Teams meetings can be available during a meeting without saving a transcript. To use Copilot during and after a meeting, transcription must be started. Review your organization's Teams meeting policies and decide which Copilot meeting experiences should be available to users. Consider whether your requirements allow meeting transcripts to be saved.

**Why review this configuration:**

- Determines whether users can use Copilot during a meeting, after a meeting, or both.
- Affects whether a saved transcript is available to support Copilot after the meeting.
- Helps your organization align Copilot meeting experiences with its transcription and retention requirements.

For more information, see [Manage Microsoft Copilot in Teams meetings and events](https://learn.microsoft.com/en-us/microsoftteams/copilot-teams-transcription).

### Copilot Analytics

Copilot analytics and reporting can help your organization understand Copilot readiness, adoption, and usage.

Review the analytics experiences available to your organization and determine which stakeholders need access to Copilot reporting. Use available analytics to identify areas where you might need to add more configuration, deployment, or adoption work.

**Why review this configuration:**

- Helps your organization understand Copilot readiness and adoption.
- Provides information that can help your organization assess how Copilot is being used.
- Can help identify areas that require more deployment, configuration, or adoption work.

For more information, see [Copilot Analytics introduction](https://learn.microsoft.com/en-us/viva/insights/copilot-analytics-introduction) and [Access insights easily with ready-to-use Copilot Analytics reports](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-analytics-reports).

### Microsoft 365 feedback and logs

Microsoft 365 includes policies that control whether users can provide feedback and whether related diagnostic information is included.

Review these policies so that your feedback configuration aligns with your organization's privacy and diagnostic-data requirements.

**Why review this configuration:**

- Determines whether users can provide feedback about their Microsoft 365 experiences.
- Gives administrators control over organizational feedback policies.
- Helps organizations align feedback and diagnostic-data collection with their requirements.

For more information, see [Manage Microsoft feedback for your organization](https://learn.microsoft.com/en-us/privacy/microsoft-365/feedback/feedback-manage).

### AI providers operating as Microsoft subprocessors

Microsoft Copilot can use AI models from supported AI providers that operate as Microsoft subprocessors. Enabling AI providers in the **AI providers operating as Microsoft subprocessors** setting gives your organization greater model flexibility, including quicker access to new AI models and innovations as they become available in supported Microsoft services and Copilot experiences, while maintaining Microsoft's enterprise-grade commitments and safeguards.

**Why review this configuration:**

- Determine whether your organization wants access to supported models from AI providers operating as Microsoft subprocessors, including newer models and capabilities as they become available.
- Confirm that the providers and models you enable align with your organization's security, compliance, privacy, and governance requirements, along with any workload-specific controls that apply.

For more information, see [Overview of AI Subprocessors](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-subprocessor-overview) and [Assign AI provider access to users and groups](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-ai-provider-user-sec-group-access).

### Copilot connectors

Copilot connectors make content from supported data sources available to Microsoft Copilot, subject to user permissions, licensing, and the connector model.

Review the connectors deployed in your organization and decide which supported data sources to make available to Copilot.

**Why review this configuration:**

- Determines which supported external data sources are available to Copilot.
- Extends the organizational information available to Copilot.
- Helps administrators manage connected data sources.

For more information, see [Manage connector connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/manage-connector).

### Agent access and deployment

The Microsoft 365 admin center provides centralized controls for managing AI agents across your organization. Administrators can manage areas such as agent and plugin access, user access, sharing, and agent governance.

Review your agent configuration to determine which users should have access to agents and which agents should be available in your organization.

Consider the following areas:

- **Microsoft-built agents:** Determine whether Microsoft-provided agents should be available to users.
- **External-provider agents:** Determine which categories of externally provided agents and plugins should be available.
- **Organization-built agents:** Determine how agents created by your organization should be made available and shared.
- **Agent deployment:** Review the agents assigned or deployed to users and groups.

Apply your organization's security, compliance, governance, and deployment requirements when determining agent access.

For more information, see [Manage agents in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/manage-copilot-agents-integrated-apps).

## Keep your configuration current

Revisit your Copilot configuration as capabilities, licensing, policies, and organizational needs change. Use the configuration areas in this article to assess what should remain available, what needs adjustment, and what requires further evaluation before broader deployment.

## Related content

- [Microsoft Copilot documentation](https://learn.microsoft.com/en-us/microsoft-365/copilot/)
- [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview)
- [Requirements for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements)
