<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-essentials-overview -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Agent Management Essentials for Microsoft 365

The guidance provided within this set of content has been designed to help you view, manage, create, protect, and understand all aspects of agents in Microsoft 365.

Key aspects of this content include the following topics:

- [Prerequisites](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-prerequisites) - Understand licensing requirements, admin permissions, and access controls.
- [Blueprint](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-blueprint) - Understand how to enable Microsoft Copilot at scale.
- [Checklist](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-checklist) - Understand how to successfully implement and deploy agent governance.
- [Visual Guide](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-visual-map) - Follow the guided management paths and links to better understand agents.
- [Admin Guide](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-admin-guide) - Understand where to start when working with agents in Microsoft 365.
- [FAQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/m365-agents-faq) - Answers to common questions about agents in Microsoft 365.

Note

Microsoft Agent 365 is the control plane for AI agents, empowering your organization to confidently deploy, govern, and manage all your agents at scale, regardless of where these agents are built or acquired. For more information, see [Overview of Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/overview) and [Microsoft Agent 365 documentation](https://learn.microsoft.com/en-us/microsoft-agent-365/).

## Understand agent security, privacy, and compliance

Microsoft applies a multi-layered, defense-in-depth strategy to secure Microsoft Copilot at every level, grounded in enterprise security, privacy, and compliance standards. Each aspect of this foundation forms a safer digital ecosystem for you and your organization to confidently adopt AI features and tools.

Agents use this foundation as part of Copilot's AI [infrastructure](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture), [model](https://learn.microsoft.com/en-us/microsoft-copilot-studio/nlu-gpt-overview), and [orchestrator](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/orchestrator), which means agents adhere to the security, privacy, and compliance that is provided by Microsoft Copilot.

Note

Your organization's data is maintained within the Microsoft 365 service boundary within your tenant. For more information, see [Microsoft Copilot architecture and how it works](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture).

Copilot and agents only access data that [individual users are authorized to access](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture#user-access-and-data-privacy) and don't access data that the user don't have permission to access. In addition, Copilot and agents honors [Conditional Access policies and multifactor authentication \(MFA\) based on Microsoft Entra ID](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture#copilot-honors-conditional-access-and-mfa).

When you integrate your business workflows as agents for Copilot, your internal data stays within your agent. That data doesn't flow out of [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) and it isn't used to train Microsoft Copilot [LLMs](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-are-large-language-models-llms). Copilot does, however, generate a search query to send to your agent on the user's behalf based on their prompt and conversation history with Copilot and data the user has access to in Microsoft 365.

Microsoft's comprehensive security posture for AI includes:

- [Secure engineering and development practices](https://learn.microsoft.com/en-us/microsoft-365/copilot/security-microsoft-365-copilot)
- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)

Note

You can also use [Microsoft Purview](https://learn.microsoft.com/en-us/purview/ai-m365-copilot), which provides tools to help you discover, secure, and govern your data for use in Microsoft Copilot, Microsoft Copilot Chat, and agents published to Microsoft 365. In addition, Microsoft Purview can help discover, protect, and govern the interactions \(prompts and responses\) with these AI apps.

## Zero Trust

To prepare your Microsoft 365 environment for Copilot and agents, you should apply the principles of Zero Trust to your tenant. The seven layers of protection encompassing [Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/copilots/zero-trust-microsoft-365-copilot?toc=%2Fcopilot%2Fmicrosoft-365%2Ftoc.json&bc=%2Fcopilot%2Fmicrosoft-365%2Fbreadcrumb%2Ftoc.json#whats-in-this-article) are the following:

1. Data protection
2. Identity and access
3. App protection
4. Device management and protection
5. Threat protection
6. Secure collaboration with Teams
7. User permissions to data

For more information about preparing your Microsoft 365 environment, see [Zero Trust](https://learn.microsoft.com/en-us/security/zero-trust/copilots/zero-trust-microsoft-365-copilot?toc=%2Fcopilot%2Fmicrosoft-365%2Ftoc.json&bc=%2Fcopilot%2Fmicrosoft-365%2Fbreadcrumb%2Ftoc.json#whats-in-this-article).

## RAI

Agents follow the Responsible AI \(RAI\) requirements included with Microsoft 365. Microsoft is committed to ensuring that our AI systems are guided by our [AI principles](https://www.microsoft.com/ai/principles-and-approach/) and [Responsible AI Standard](https://www.microsoft.com/ai/responsible-ai). These principles include empowering our customers to use these systems effectively and in line with their intended uses. Our approach to responsible AI is continually evolving to address emerging issues proactively.

RAI principles include the following principles:

- Accountability
- Transparency
- Fairness
- Reliability and safety
- Privacy and security
- Inclusiveness

For more information, see [Responsible AI FAQ for Microsoft Copilot in Azure](https://learn.microsoft.com/en-us/azure/copilot/responsible-ai-faq).

## Protect organizational data

Microsoft Copilot works with different Microsoft services to help you protect your organization's data. When you're ready to deploy agents within your organization, you should consider Microsoft's recommended approach to address oversharing concerns. This approach provides the pilot, deploy, and operate phases to consider when deploying Copilot and agents. Each phase consists of activities, outcomes, and expected effort needed. For more information, see [Secure & governed data foundation for Microsoft Copilot: A deployment blueprint](https://learn.microsoft.com/en-us/microsoft-365/copilot/secure-govern-copilot-foundational-deployment-guidance).

In addition, Microsoft provides SharePoint Advanced Management and Microsoft Purview to address oversharing. SharePoint Advanced Management provides SharePoint site management and content governance capabilities. Microsoft Purview provides security, compliance, and governance across data and files.

Note

Microsoft Copilot uses the access rights of the end user to determine the data that can be presented to the end user.

To better understand aspects of data protection related to Microsoft Copilot, such as sensitivity labels, encryption, oversharing, and data auditing, see the following resources:

- [How data is protected and audited in Microsoft 365 and Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture-data-protection-auditing)
- [Enterprise data protection in Microsoft Copilot and Microsoft Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection)
- [Considerations to manage Microsoft Copilot and Channel Agent in Teams for security and compliance](https://learn.microsoft.com/en-us/purview/ai-m365-copilot-considerations)
