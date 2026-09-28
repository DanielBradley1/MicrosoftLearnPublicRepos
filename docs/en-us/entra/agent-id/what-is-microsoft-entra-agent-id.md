<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/what-is-microsoft-entra-agent-id -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# What is Microsoft Entra Agent ID?

Microsoft Entra Agent ID is an identity and security framework that extends Microsoft Entra capabilities to AI agents. As organizations deploy assistive, autonomous, and user-like agents, they need purpose-built identity constructs to authenticate, authorize, govern, and protect these nonhuman identities. Microsoft Entra Agent ID addresses these needs by providing a unified platform for managing agent identities at enterprise scale.

[![Diagram showing the identity management, access protection, governance, and compliance capabilities that Microsoft Entra Agent ID provides for AI agents.](https://learn.microsoft.com/en-us/entra/agent-id/media/what-is-microsoft-entra-agent-id/microsoft-entra-agent-identity-capabilities.png)](https://learn.microsoft.com/en-us/entra/agent-id/media/what-is-microsoft-entra-agent-id/microsoft-entra-agent-identity-capabilities-expanded.png#lightbox)

Microsoft Entra Agent ID brings together identity management, access protection, governance, and compliance for AI agents.

## Agent identity platform

The [Microsoft Entra Agent identity platform](https://learn.microsoft.com/en-us/entra/agent-id/what-is-agent-id-platform) enables developers to create and manage [agent identities](https://learn.microsoft.com/en-us/entra/agent-id/what-are-agent-identities), which are specialized identity constructs built for AI agents. Agent identity blueprints serve as templates for creating individual agent identities with parent-child relationships, enabling consistent security policies across large numbers of agents. The platform supports standard protocols such as OAuth 2.0, Model Context Protocol \(MCP\), and agent-to-agent \(A2A\) for authentication and agent-to-agent communication.

Microsoft Entra Agent ID works with agents built on Microsoft and non-Microsoft platforms. Organizations can [integrate third-party agents](https://learn.microsoft.com/en-us/entra/agent-id/configure-third-party-agents) from platforms such as AWS Bedrock and n8n by using the Microsoft Entra ID Auth SDK \(sidecar\) or workload identity federation, giving every agent a governed identity regardless of where it was built.

## Security and governance for agents

Microsoft Entra Agent ID extends existing Microsoft Entra security and governance capabilities to agent identities. Agents receive the same identity-driven protections as users and workloads, including adaptive access policies, real-time risk detection, lifecycle management, and network-level controls. All agent authentication and activity is logged for compliance and audit.

For details on how these capabilities work for agents, see:

- [Microsoft Entra security for AI overview](https://learn.microsoft.com/en-us/entra/agent-id/security-for-ai-overview)
- [Conditional Access for agents](https://learn.microsoft.com/en-us/entra/identity/conditional-access/agent-id)
- [Identity Protection for agents](https://learn.microsoft.com/en-us/entra/id-protection/concept-risky-agents)
- [Identity governance for agents](https://learn.microsoft.com/en-us/entra/id-governance/agent-id-governance-overview)
- [Network controls for agents](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-secure-web-ai-gateway-agents)
- [Sign-in and audit logs for agents](https://learn.microsoft.com/en-us/entra/agent-id/sign-in-audit-logs-agents)

## How to get started

Microsoft Entra Agent ID is a product within Microsoft Entra that provides the platform for creating and managing agent identities and agent identity blueprints. Agent ID is available for all Microsoft Entra customers.

[Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/overview) enables agents to operate across Microsoft 365 services and enterprise workflows, which requires a **Microsoft Agent 365** license for each user. For pricing details, see [Microsoft Agent 365 plans and pricing](https://www.microsoft.com/microsoft-agent-365#plans-and-pricing).

Extending Microsoft Entra security features to agents requires Microsoft Agent 365. Agent 365 is included with Microsoft 365 E7 and is available as an add-on to Microsoft E5/A5/Business Premium \(or Microsoft Defender Suite + Microsoft Purview Suite\). See our latest [Agent 365 product terms for more details](https://www.microsoft.com/licensing/terms/productoffering/Agent365/EAEAS#clause-2755-h3-1).

## Related content

- [Microsoft Entra security for AI overview](https://learn.microsoft.com/en-us/entra/agent-id/security-for-ai-overview)
- [What are agent identities?](https://learn.microsoft.com/en-us/entra/agent-id/what-are-agent-identities)
- [What is the Microsoft Entra Agent identity platform?](https://learn.microsoft.com/en-us/entra/agent-id/what-is-agent-id-platform)
