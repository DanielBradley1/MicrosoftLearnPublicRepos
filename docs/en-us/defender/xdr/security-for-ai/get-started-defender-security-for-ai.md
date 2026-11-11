<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/get-started-defender-security-for-ai -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Enable security for AI agents using Microsoft Defender

Microsoft Defender integrates with [Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/overview) to secure the AI agents in your organization. After you onboard to Agent 365, enable security for AI agents to discover, protect, and respond to threats targeting agents in your tenant. For an overview of the agent security capabilities, see [Protect AI agents using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/defender-security-for-ai#protect-ai-agents-using-microsoft-defender).

Onboarding includes enabling data collection, connecting the Microsoft 365 app connector, and onboarding Copilot Studio for real-time protection.

## Prerequisites

Local agents are onboarded separately from cloud agents. For local AI agent discovery, meet the [discovery prerequisites](https://learn.microsoft.com/en-us/defender-endpoint/discover-local-ai-agents#prerequisites). Discovery doesn't require you to enable AI agent runtime protection. To configure runtime protection separately, see [Set up AI agent runtime protection](https://learn.microsoft.com/en-us/defender-endpoint/configure-ai-agent-runtime-protection).

Before you onboard cloud agents, make sure you have:

- [Onboard to Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/overview).
- Security Administrator role or higher in Microsoft Entra ID.
- For Copilot Studio real-time protection, you need collaboration with a Power Platform administrator.

## Connect data sources

To configure the data sources that Microsoft Defender uses to surface, investigate, and protect AI agents in your tenant:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Go to **Settings** > **Security for AI** > **Get started**.

   When you onboard to Agent 365, security for AI agents is enabled automatically, including AI agent discovery, security posture assessment, and threat detection. The **Enable** toggle is on by default. To stop collecting data for AI agents, switch it to **Off**.

   A setup checklist shows the status of required and optional data sources. **Agent 365** provides unified visibility into AI agents and is marked as **Done** automatically.
3. Enable the Microsoft 365 connector to get [investigation and advanced hunting capabilities](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-detection-protection) for AI agent activity:

   1. In the **Get started** page, select the **Microsoft 365 connector** step.
   2. On the **Select Microsoft 365 components** step, select at least the two components required for AI agent monitoring:

      - **Microsoft Entra ID Management events**: audit admin activities performed in Microsoft Entra ID.
      - **Microsoft 365 activities**: audit activities performed by users in your Microsoft 365 apps.


      **Microsoft Entra Users and groups** is a prerequisite for all monitoring capabilities and is selected by default.

   3. Select **Connect Microsoft 365** to complete the connector setup.


   When the connector is active, its status shows as **Connected**.


   Note


   For Copilot Studio agents, if the Microsoft 365 connector isn't connected, alerts and incidents related to these actions don't appear in the Microsoft Defender portal.

## Next steps

After onboarding is complete, explore these capabilities:

- [Discover AI agents and assess security posture using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-inventory)
- [Detect and investigate threats to AI agents using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-detection-protection)
- [Protect AI agents in real time using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-real-time-protection)
