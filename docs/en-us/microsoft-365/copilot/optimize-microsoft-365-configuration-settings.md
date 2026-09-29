<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/optimize-microsoft-365-configuration-settings -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Optimize Microsoft Copilot configuration settings

Note

**The Microsoft 365 Copilot app is now called Microsoft Copilot**. The primary URL for accessing the updated Copilot app is changing from `m365.cloud.microsoft` to `copilot.cloud.microsoft`. To help ensure users' connections aren't blocked, see [recommended network configurations for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-requirements#network-requirements).

Configure your tenant for the best Microsoft Copilot experience. This article describes ten priority configuration settings that improve adoption, satisfaction, and retention, and explains where to find them in the Microsoft 365 admin center.

This video provides an overview of how the recommended configuration settings can help to optimize Microsoft Copilot in your business.

<iframe src="https://learn-video.azurefd.net/vod/player?id=7c10ece9-f661-4132-a53a-0a214c960b63" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Why configuration matters

Proper configuration of Copilot tenant settings is critical so users can fully benefit from Copilot. Tenants that are correctly configured show measurable improvements in usage, engagement, and satisfaction. Configuring these settings helps move tenants from at‑risk to healthy states and supports better governance, compliance, and AI‑powered productivity outcomes.

## Recommended Copilot tenant settings

The following ten settings are the most critical configurations for Copilot success.

[![Diagram that shows the recommended Copilot configuration settings for admins.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/recommended-copilot-settings.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/recommended-copilot-settings.png#lightbox)

### Web Search

The *Web Search* setting allows Microsoft Copilot to retrieve real‑time public information from the web.

This setting generates search queries from user prompts and using results from services like Bing to enrich responses, combining web data with organizational context while remaining governed by admin controls and security policies.

**Why this setting matters**:

- Retrieves current public information to enhance response accuracy
- Reduces reliance on outdated training data
- Combines web and organizational data for more complete, relevant results

For more information about this setting, see [Data, privacy, and security for web search in Microsoft Copilot and Microsoft Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-public-web-access).

### Microsoft Copilot app pinned to Windows taskbar

The *Microsoft Copilot app pinned to Windows taskbar* setting places the Microsoft Copilot app on the Windows taskbar. This setting makes Copilot more visible and accessible on users' desktops.

**Why this setting matters**:

- Provides a consistent, one‑click entry point to Copilot outside Microsoft 365 apps
- Reduces friction for users, making Copilot easier to access and increasing adoption
- Helps standardize the Copilot experience across devices for better admin manageability

For more information, see [Pin Microsoft Copilot and its companion apps to the Windows taskbar](https://learn.microsoft.com/en-us/microsoft-365/copilot/pin-copilot-taskbar).

### Core 1P Agents

The *Core 1P Agents* setting controls whether Microsoft-provided agents, such as the Researcher agent, are available to users in Microsoft Copilot experiences.

When this setting is enabled, users can access the Researcher agent to perform advanced, multi-step research using Copilot. If it is restricted, access to these Microsoft-built agents \(including Researcher\) is limited based on the configured policy.

**Why this setting matters**:

- Enables Copilot to deliver deeper, high‑value insights using advanced reasoning
- Combines multiple data sources to improve the quality and depth of analysis
- Increases trust through transparent, cited responses while supporting complex research tasks

For more information, see [Manage agents in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).

### Teams Meeting Transcription

The *Teams Meeting Transcription* setting captures meeting conversations as structured text that Microsoft Copilot uses to generate summaries, action items, and meeting Q&A.

This setting provides the grounded data Copilot needs to analyze meeting content, improving accuracy, knowledge reuse, and access to insights during and after the meeting.

**Why this setting matters**:

- Provides structured data that enables Copilot to generate summaries, action items, and Q&A
- Improves accuracy and supports long-term knowledge reuse across meetings
- Ensures transcripts are governed artifacts aligned with organizational security and data protection policies

For more information, see [Manage Microsoft Copilot in Teams meetings and events](https://learn.microsoft.com/en-us/microsoftteams/copilot-teams-transcription).

### Channel Readiness

The *Channel Readiness* setting ensures that Microsoft 365 apps receive the latest Copilot features, updates, and fixes so the service remains fully functional and consistent for users.

This setting keeps apps on eligible release channels that deliver Copilot capabilities reliably, helping ensure compatibility, performance, and ongoing access to new Copilot experiences.

**Why this setting matters**:

- Ensures Copilot features are available, functional, and consistently delivered
- Keeps users on the latest capabilities while improving security, reliability, and performance
- Helps admins balance innovation with control by managing feature rollout at scale

For more information, see [Change update channel of Microsoft 365 Apps to enable Copilot](https://learn.microsoft.com/en-us/microsoft-365-apps/updates/change-channel-for-copilot).

### Microsoft 365 Feedback & Logs

The *M365 Feedback & Logs* setting enables users and admins to submit feedback and diagnostic data, creating a continuous feedback loop that helps improve Microsoft Copilot performance and user experience over time.

This setting captures insights from real user interactions and issues, allowing Microsoft to refine Copilot responses, accelerate issue resolution, and give admins visibility into adoption challenges and user experience trends.

**Why this setting matters**:

- Creates a continuous feedback loop that improves Copilot performance and user experience
- Provides Microsoft with actionable insights and diagnostic data to enhance product quality
- Gives admins visibility into user experiences and adoption challenges to inform targeted support

For more information, see [Manage Microsoft feedback for your organization](https://learn.microsoft.com/en-us/privacy/microsoft-365/feedback/feedback-manage).

### Anthropic as a sub‑processor

The *Anthropic as a sub‑processor* setting allows Microsoft Copilot to use additional AI models \(such as Claude\) from Anthropic alongside Microsoft models, expanding flexibility, reasoning capabilities, and output quality while remaining within Microsoft's compliance framework.

This setting lets admins control whether these external models are available in Copilot, enabling more advanced scenarios like deep analysis and multi-step workflows while maintaining governance, security, and policy enforcement across the tenant.

**Why this setting matters**:

- Enables use of multiple AI models within Copilot while remaining within Microsoft's compliance framework
- Improves output quality for complex and advanced scenarios
- Future‑proofs deployments with multi‑model innovation under enterprise governance

For more information, see [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor).

### Usage-based billing

When you enable **AI experiences enabled by usage-based billing**, features that rely on usage-based billing will be visible to users across the tenant.

Microsoft uses a usage-based billing model that uses Copilot Credits to provide flexible payment options alongside fixed licensing. This model enables organizations to manage and optimize AI service expenses effectively through centralized tools like the Cost management dashboard in the Microsoft 365 admin center.

**Why this setting matters**

- Helps organizations control AI spending by defining who can access usage-based AI experiences and how Copilot Credits are consumed
- Prevents unexpected costs through spending limits, budgets, alerts, that help administrators manage usage proactively
- Creates clear operational guardrails that enable organizations to scale AI adoption confidently while maintaining budget accountability

For more information, see [Managing AI experiences enabled by usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits).

### Copilot in Microsoft 365 apps with Anthropic models

The *Copilot in Microsoft 365 apps with Anthropic models* setting allows Copilot to use Anthropic models within apps like Word, Excel, and PowerPoint, improving reasoning, structure, and output quality for everyday work scenarios.

This setting lets Copilot select the most suitable AI model for each task directly within Microsoft 365 apps, enabling more advanced document creation, data analysis, and multi-step workflows while remaining centrally governed by Microsoft 365 policies.

**Why this setting matters**:

- Enables Copilot to select the most suitable AI model for each task
- Improves reasoning, structure, and overall output quality across scenarios
- Enhances document creation, data analysis, and multi-step workflows within a centralized, governed Microsoft 365 environment

For more information, see [Copilot in Microsoft 365 apps with Anthropic models](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-anthropic-apps).

### Copilot Connectors

The *Copilot Connectors* setting enables Microsoft Copilot to access and use data from third‑party systems, extending its knowledge beyond Microsoft 365 to provide richer, more context-aware responses.

This setting integrates external data sources with Copilot.

**Why this setting matters**:

- Extends Copilot beyond Microsoft 365 by integrating data from third‑party systems
- Improves response accuracy, relevance, and depth with richer organizational context
- Preserves existing security and compliance controls while expanding data access

For more information, see [Manage Connector connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/manage-connector).

### Copilot Frontier

The *Copilot Frontier* setting gives organizations early access to new and upcoming Copilot capabilities, such as advanced AI features, agents, and multi-step workflows before they are generally available.

This setting allows admins to selectively enable preview features for users.

**Why this setting matters**:

- Provides early access to the latest Copilot innovations before general availability
- Helps admins evaluate and prepare for upcoming features in advance
- Enables controlled rollout and feedback to shape future experiences while managing risk

For more information, see [Get started with the Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier).

## Impact for admins

Configuring these settings enables administrators to:

- Drive Copilot adoption and usage across the organization.
- Improve user satisfaction and productivity outcomes.
- Meet data security, compliance, and governance requirements.
- Identify configuration gaps using tenant health insights.
- Prioritize remediation based on measurable impact.
- Support continuous improvement through feedback and analytics.

## Best practices

- Review Copilot configuration status in the Microsoft 365 admin center on a regular cadence.
- Use tenant health scoring to track progress over time.
- Engage stakeholders to align on security and compliance policies.
- Monitor adoption metrics and adjust configurations accordingly.
- Stay current on new Copilot features and configuration requirements.

## Related content

- [Microsoft Copilot minimum requirements](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements)
- [Microsoft Copilot data and compliance readiness](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements-data-compliance)
- [Manage Microsoft Copilot scenarios in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-page)
