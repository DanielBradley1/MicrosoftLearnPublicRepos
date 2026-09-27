<!-- Source: https://learn.microsoft.com/en-us/intune/copilot/agents/ -->
<!-- Sitemap-Last-Modified: 2026-04-01 -->

# Security Copilot agents in Intune overview

Security Copilot agents in Intune are AI-powered assistants that enhance enterprise security. They automate tasks for endpoint protection, identity management, threat intelligence, and device configuration. They help IT teams quickly address vulnerabilities, policy gaps, and emerging threats.

Agents are built on Microsoft Security Copilot's generative AI and automation capabilities. They observe, reason, and act with oversight and review from your administrators. Each agent is tailored to a specific use case, operates within the Intune admin center, and uses role-based access controls.

## Available agents

Microsoft Intune includes specialized Security Copilot agents, each designed for a specific security scenario. The following agents are available:

#### Change Review Agent

![](https://learn.microsoft.com/en-us/intune/copilot/agents/icons/change-review-agent.svg)

> The *Change Review Agent* evaluates the effect of approval requests in Intune and makes recommendations for the actions you can take.
> 
> [Learn more](https://learn.microsoft.com/en-us/intune/copilot/agents/change-review-agent)

#### Device Offboarding Agent

![](https://learn.microsoft.com/en-us/intune/copilot/agents/icons/device-offboarding-agent.svg)

> The *Device Offboarding Agent* identifies stale or misaligned devices across Intune and Microsoft Entra ID, providing actionable insights and requiring admin approval before offboarding any devices.
> 
> [Learn more](https://learn.microsoft.com/en-us/intune/copilot/agents/device-offboarding-agent)

#### Policy Configuration Agent

![](https://learn.microsoft.com/en-us/intune/copilot/agents/icons/policy-configuration-agent.svg)

> With the *Policy Configuration Agent*, you import documents or write instructions in plain language. The agent uses this information to find matching settings in the Intune settings catalog and recommends values for these settings. You can then use the agent to create a policy with those settings and their values.
> 
> [Learn more](https://learn.microsoft.com/en-us/intune/copilot/agents/policy-configuration-agent)

#### Vulnerability Remediation Agent

![](https://learn.microsoft.com/en-us/intune/copilot/agents/icons/vulnerability-remediation-agent.svg)

> The *Vulnerability Remediation Agent* uses Defender data to monitor vulnerabilities and prioritize remediation with AI-driven risk assessments.
> 
> [Learn more](https://learn.microsoft.com/en-us/intune/copilot/agents/vulnerability-remediation-agent)

## Getting started with agents

### Prerequisites

Before you begin, make sure you have:

- [Security compute units \(SCU\)](https://learn.microsoft.com/en-us/copilot/security/manage-usage) available
- Reviewed the [Privacy and data security in Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/privacy-data-security) to understand how your data is handled.

### Setup process

1. Enable Security Copilot using the [Security Copilot setup guide](https://learn.microsoft.com/en-us/copilot/security/get-started-security-copilot).
2. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) using the least privileged role required for the agent you want to configure.
3. Browse to **Agents** and select **View details** for the agent you want to configure.

[![Screenshot of the security copilot feature in the Intune admin center.](https://learn.microsoft.com/en-us/intune/copilot/agents/media/index/security-copilot-agents.png)](https://learn.microsoft.com/en-us/intune/copilot/agents/media/index/security-copilot-agents.png#lightbox)

## Agents in the Microsoft ecosystem

While this article focuses on Intune agents, similar agents are available across other Microsoft security products. For more information, see:

- [Microsoft Entra](https://learn.microsoft.com/en-us/entra/security-copilot/entra-agents)
- [Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-agents-defender)
- [Microsoft Purview](https://learn.microsoft.com/en-us/purview/copilot-in-purview-agents)

## Related content

- [Microsoft Security Copilot agents overview](https://learn.microsoft.com/en-us/copilot/security/agents-overview)

## ![](https://learn.microsoft.com/en-us/intune/media/icons/32/feedback.svg) Help shape the future of Intune agents

Join our **Intune Agents Feedback Forum** to share insights and influence upcoming capabilities in Microsoft Intune.

Sign up and learn more: [https://aka.ms/IntuneAgentsForum](https://aka.ms/IntuneAgentsForum)
