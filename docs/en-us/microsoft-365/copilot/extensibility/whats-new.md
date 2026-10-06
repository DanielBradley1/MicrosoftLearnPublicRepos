<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/whats-new -->
<!-- Sitemap-Last-Modified: 2026-08-27 -->

# What's new in Microsoft 365 Copilot extensibility

As a developer, you can extend, enrich, and customize [Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/microsoft-365-copilot-overview) for the unique way your customers work. This article provides the latest information about what's new in Microsoft 365 Copilot extensibility.

For the latest information, announcements, and news about preview and generally available \(GA\) features, follow the [Microsoft 365 Copilot developer blog](https://devblogs.microsoft.com/microsoft365dev/category/microsoft-365-copilot/).

## August 2026

### Review requested packages in the Package Management API

Administrators can review the agents that users in the organization requested by filtering [List packages](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackages-list) on the `requestStatus` or `requestType` property.

## July 2026

### Declarative agent manifest version 1.8

A new version of the declarative agent manifest schema is available. [Declarative agent manifest schema version 1.8](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8) adds the following features:

- Added the new `EmailActions` capability to enable write operations on email such as triage, supervised send, delete, inbox rules, auto-reply, and folder management.
- Added the new `MeetingActions` capability to enable meeting and calendar actions such as scheduling events, creating time-finding polls, and surfacing time insights.
- Added the `file` property to the worker agent object as an alternative to `id` for referencing worker agents by file path.
- Added the `embedded_resource_snapshot_id` property to the embedded knowledge object.

### New version parameter for Copilot usage reports API

A `version` parameter is added to the [getMicrosoft365CopilotUserCountSummary](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/reports/copilotreportroot-getmicrosoft365copilotusercountsummary), [getMicrosoft365CopilotUserCountTrend](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/reports/copilotreportroot-getmicrosoft365copilotusercounttrend), and [getMicrosoft365CopilotUsageUserDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/reports/copilotreportroot-getmicrosoft365copilotusageuserdetail) APIs that developers can use to request extra information in the generated reports.

## May 2026

### OneDrive knowledge in Agent Builder

Add folders and up to 50 OneDrive files as knowledge when you use Agent Builder in Microsoft 365 Copilot to build your agent. For more information, see [Add knowledge sources](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-knowledge).

### Set default response mode in Agent Builder

When you build an agent in Agent Builder in Microsoft 365 Copilot, you can now set the default response mode for your agent. For more information, see [Set the default response mode](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents#set-the-default-response-mode).

### Declarative agent manifest version 1.7

A new version of the declarative agent manifest schema is available. [Declarative agent manifest schema version 1.7](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.7) adds the following features:

- Added the optional `editorial_answers` property so agents can match semantically similar user queries to predefined question and answer pairs.
- Added the optional `default_response_mode` property to the [Behavior overrides object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.7#behavior-overrides-object) so you can set the agent's default mode to `Auto`, `Think deeper`, or `Quick response`.
- Added the optional `depends_on` property to the [Conversation starters object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.7#conversation-starters-object) to specify capability dependencies for conversation starters.

### New agent templates added to Agent Builder

Agent Builder now includes eight new agent templates to help you quickly build declarative agents for common workplace scenarios:

- [AI Learning Advisor](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-ai-learning-advisor)
- [Executive Briefing Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-executive-briefing)
- [My Company Policy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-my-company-policy)
- [Personal News Digest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-personal-news-digest)
- [Plan My Day](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-plan-my-day)
- [Project Delta Digest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-project-delta-digest)
- [SME Finder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-sme-finder)
- [Status Update Agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-template-status-update-agent)

For more information, see [Agent templates overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-templates-overview).

### Evaluate agents

Evaluate agents by using a comprehensive evaluation framework and tooling to refine agent performance. The Agent Evaluations CLI tool enables developers to create, run, and analyze tests for their agents. For more information, see [Agent evaluation overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluation-overview) and [Agent Evaluations CLI overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/evaluations-cli-overview).

### Package Management API updates \(preview\)

The Package Management API has new capabilities for IT administrators to manage apps and agents in their Microsoft 365 organization. Administrators can now block and unblock packages to control their availability, update package metadata, and reassign package ownership. For more information, see [Package Management API overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/overview).

## April 2026

### Agent Registration API \(preview\)

The Agent Registration API enables developers and administrators to programmatically register and manage agents within their Microsoft 365 environment. The API supports creating, retrieving, updating, and deleting agent registrations with associated metadata and agent cards. For more information, see [Agent Registration API overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/overview).

### Copilot policy settings API \(preview\)

The Copilot policy settings API is now available in preview. This API provides a unified endpoint to read and update Copilot settings across multiple policy services, including Cloud Policy Service \(CPS\) and Microsoft Intune. For more information, see [copilotPolicySetting resource type](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/resources/copilotpolicysetting).

## March 2026

### Share agents to teams in Microsoft Teams

You can now share agents built with Agent Builder in Microsoft 365 Copilot to teams as well as users and groups. For more information, see [Share and manage agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-share-manage-agents).

### Use natural language to create an agent in Microsoft 365 Copilot

You can now create agents more quickly with Agent Builder in Microsoft 365 Copilot by using natural language. The agent is automatically configured for you. For more information, see [Use natural language to describe your agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-build-agents#use-natural-language-to-describe-your-agent-recommended).

### Interactive UI widgets for declarative agents

You can now add interactive UI widgets to your declarative agents by extending MCP server-based actions using the [OpenAI Apps SDK](https://developers.openai.com/apps-sdk). Widgets can render inline or in full-screen mode within Microsoft 365 Copilot. For more information, see [Add MCP apps to declarative agents in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-mcp-apps).

## February 2026

### Agent Builder availability in GCCH

Agent Builder is now available in Government Community Cloud High \(GCCH\) environments.

## January 2026

### Retrieval API pay-as-you-go consumption \(preview\)

The Microsoft 365 Copilot Retrieval API is now available to users without a Microsoft 365 Copilot add-on license via pay-as-you-go consumption \(preview\). This model provides access to the Retrieval API for tenant-level data sources such as SharePoint and Microsoft 365 Copilot connectors. For more information, see [Microsoft 365 Copilot Retrieval API pay-as-you-go consumption \(preview\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/retrieval/paygo-retrieval).

## Related content

- [Microsoft 365 Copilot extensibility overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview)
- [What's new history](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/whats-new-history)
