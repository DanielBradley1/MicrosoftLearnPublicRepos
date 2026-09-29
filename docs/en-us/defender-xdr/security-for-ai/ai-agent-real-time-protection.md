<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-real-time-protection -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Protect AI agents in real time using Microsoft Defender

Deployed AI agents operate autonomously, invoking tools, accessing data, and taking actions in response to natural‑language input. Microsoft Defender provides real-time protection to prevent AI agents from performing unsafe actions during runtime, and lets you control that protection using policies and rules.

To detect, investigate, and hunt for AI agent threats after they occur, see [Detect and investigate threats to AI agents using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-detection-protection).

## Prerequisites

- Enable security for AI agents, including the Microsoft 365 app connector. See [Enable security for AI agents using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/get-started-defender-security-for-ai).
- To protect Copilot Studio agents in real time, make sure Copilot Studio is connected. See [Enable security for AI agents using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/get-started-defender-security-for-ai).
- Local agents are onboarded separately from cloud agents. To protect local AI agents that run on endpoints, set up [AI agent runtime protection in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/configure-ai-agent-runtime-protection). Microsoft Defender for Endpoint must run in active mode.

## How real-time protection works

Real-time protection inspects AI agent activity throughout the agentic loop and blocks risky actions before they execute. Coverage depends on the agent type:

- **Agent 365 tool invocations**: Defender integrates with [Work IQ MCP](https://learn.microsoft.com/en-us/microsoft-agent-365/tooling-servers-overview) to evaluate tool invocations before they run, including invocations of customer MCP tools [onboarded to Agent 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-tools-for-agent). Agents that rely on unsupported tools or don't integrate with Work IQ MCP aren't covered.
- **Copilot Studio agents \(Preview\)**: Protection evaluates tool invocations, which doesn't depend on Work IQ MCP. To enable it, make sure that Copilot Studio is connected. For more information, see [Enable security for AI agents using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/get-started-defender-security-for-ai).
- **Foundry agents \(Preview\):** Protection evaluates user requests, agent responses, tool invocations, and tool responses.
- **Local AI agents**: Covered through [endpoint runtime protection in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/ai-agent-runtime-protection-overview).

For cloud agents, there are two types of real-time protection rules:

- **Default rule**: Audits all agents, recording matching activity as a behavior without stopping the action. This gives you visibility before you enforce blocking.
- **Custom rules**: Block matching actions before they execute and record the behavior. Create custom rules for high-confidence threats and scope them to specific agents.

When Microsoft Defender audits or blocks an action, it records the event as a behavior in the `BehaviorInfo` table, including what happened, why the action was considered risky, and which agent, user, and tool were involved. Security teams can query these behaviors to build custom detections, hunting queries, and downstream automation. Near-real-time detections continue to surface as alerts only in audit mode. When a blocking rule covers an agent, near-real-time alerts aren't generated for that agent.

Note

Block events from Microsoft Prompt Shields for Foundry and Microsoft Copilot Agent Builder are also recorded as behaviors. This isn't yet supported for agents built with Microsoft Copilot Studio.

## Configure real-time protection rules

To view and manage rules, go to **Settings** > **Security for AI** > **Policies & rules** > **Real-time protection**. A built-in **Default** rule audits all agents. You can create custom rules to block specific detection types and scope them to specific agents.

[![Screenshot of the Real-time protection page in the Microsoft Defender portal showing the list of rules with status, type, action, and scope columns.](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/real-time-protection-rules-list.png)](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/real-time-protection-rules-list.png#lightbox)

### Create a real-time protection rule

To create a blocking rule:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Go to **Settings** > **Security for AI** > **Policies & rules** > **Real-time protection**.
3. Select **Create rule**.
4. On the **Rule details** step, set the rule **Status**, enter a **Rule name** and **Rule description**, then select **Next**.

   [![Screenshot of the Create rule wizard Rule details step with the status toggle, rule name, and rule description fields.](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/create-rule-details.png)](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/create-rule-details.png#lightbox)
5. Configure the rule scope and detection types:

   - **Scope**: Choose whether the rule applies to **All** agents or to specific agents.
   - **Exclude**: To exempt specific agents from the rule, choose the agents to exclude. You can filter the list by platform and publish status. Only agents with a Microsoft Entra agent ID appear in the list.

     [![Screenshot of the Choose agents to exclude pane with a platform filter and a list of agents that have an Entra agent ID.](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/create-rule-exclude-agents.png)](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/create-rule-exclude-agents.png#lightbox)
   - **Detection types**: Select the threat scenarios that the rule applies to, then select **Apply**.

     [![Screenshot of the detection types dropdown showing Secret exfiltration, Malicious content propagation, Evasion techniques, and Unsafe email domain.](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/create-rule-detection-types.png)](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/create-rule-detection-types.png#lightbox)

6. Select **Next**.
7. Confirm the rule name, description, action, scope, detection rules, and status, then select **Create**.

   [![Screenshot of the Review and create step summarizing the rule name, description, action, scope, detection rules, and status.](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/create-rule-review.png)](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/create-rule-review.png#lightbox)

### Manage existing rules

On the **Real-time protection** page, select a rule to open its details pane, where you can review the rule configuration and select **Edit rule** to change it. Use **Enable**, **Disable**, and **Delete** in the toolbar to manage rules.

[![Screenshot of the Real-time protection page with a rule selected and the details pane showing the action, scope, and detection rules.](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/real-time-protection-rule-details.png)](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/real-time-protection-rule-details.png#lightbox)

## Control prompt evidence in alerts

By default, Microsoft Defender includes prompt snippets exchanged between the user and the agent as evidence in each alert.

To configure this setting, go to **Settings** > **Security for AI** > **Prompt evidence collection**, then toggle **Enabled** on or off.

When enabled, the snippets include only the portions of user prompts or agent responses identified as suspicious and relevant to security classification. Sensitive data and secrets are redacted; however, customer conversations might still be sensitive in nature. The evidence is available in the Defender portal as part of each alert.

[![Screenshot of the Prompt evidence collection page with the Enabled toggle and a description of how prompt snippets are surfaced in alerts.](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/prompt-evidence-collection.png)](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/media/ai-agent-real-time-protection/prompt-evidence-collection.png#lightbox)

## Next steps

- [Detect and investigate threats to AI agents using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-detection-protection)
- [Discover AI agents and assess security posture using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/ai-agent-inventory)
- [Protect AI assets from emerging threats and vulnerabilities using Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/defender-security-for-ai)
