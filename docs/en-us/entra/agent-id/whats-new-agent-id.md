<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/whats-new-agent-id -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# What's new in Microsoft Entra Agent ID

Microsoft Entra Agent ID is now generally available. This release brings first-class identity and access management to AI agents, enabling organizations to authenticate, authorize, govern, and protect agent identities at enterprise scale. Microsoft Entra Agent ID extends Zero Trust principles to AI workloads with purpose-built identity constructs, specialized OAuth flows, and comprehensive security controls.

This article summarizes the key capabilities and documentation currently available.

## Manage AI agents at scale

Microsoft Entra Agent ID introduces new identity constructs and authentication protocols designed specifically for AI agents. Notable updates include:

- [Key concepts](https://learn.microsoft.com/en-us/entra/agent-id/key-concepts) - New concepts added to further define core agent identity concepts and their relationships.
- [Administrative relationships](https://learn.microsoft.com/en-us/entra/agent-id/agent-owners-sponsors-managers) - Deeper definitions and clarified differences between owners, sponsors, and managers of agent identities, blueprints, and agents' user accounts.
- [Design patterns](https://learn.microsoft.com/en-us/entra/agent-id/concept-agent-id-design-patterns) \(New\) - Common architectural patterns for agent identity deployments.
- [Best practices](https://learn.microsoft.com/en-us/entra/agent-id/best-practices-agent-id) \(New\) - Recommended approaches for agent identity management.
- [Plan your agent identity architecture](https://learn.microsoft.com/en-us/entra/agent-id/how-to-plan-agent-identity-architecture) \(New\) - Guidance for planning agent identity deployment at scale.
- [Create an agent identity blueprint](https://learn.microsoft.com/en-us/entra/agent-id/create-blueprint) and [Create an agent identity](https://learn.microsoft.com/en-us/entra/agent-id/create-delete-agent-identities) \(Preview\) - Use the new "wizard" to create agent identity blueprints and agent identities in the Microsoft Entra admin center.
- [AI-guided setup](https://learn.microsoft.com/en-us/entra/agent-id/agent-id-ai-guided-setup) \(New\) - Automate onboarding with an AI coding agent that walks you through blueprint creation, credential configuration, and agent identity provisioning.
- [Agent identity deletion](https://learn.microsoft.com/en-us/entra/agent-id/concept-agent-identity-deletion) \(New\) - Learn about the automated cascade cleanup process and soft-delete functionality for agent identities.
- [Authentication with the Auth SDK \(sidecar\)](https://learn.microsoft.com/en-us/entra/agent-id/authentication-with-auth-sdk-sidecar) \(New\) - Overview of the sidecar pattern for agent authentication.
- [Configure Microsoft Entra ID Auth SDK \(sidecar\) for agent identities](https://learn.microsoft.com/en-us/entra/agent-id/microsoft-entra-sdk-for-agent-identities) - SDK configuration for token acquisition.
- [Run the sidecar for local development](https://learn.microsoft.com/en-us/entra/agent-id/sidecar-local-development) \(New\) - Local development setup for the Auth SDK.
- [Validate agent tokens in a downstream API](https://learn.microsoft.com/en-us/entra/agent-id/how-to-validate-agent-tokens-downstream-api) \(New\) - Token validation guidance for APIs that receive agent tokens.
- [Configure non-Microsoft agents with Agent ID](https://learn.microsoft.com/en-us/entra/agent-id/configure-third-party-agents) \(New\) - Integration patterns \(sidecar and federation\) for platforms like AWS, GCP, and n8n.
- [Secure an Amazon Bedrock agent](https://learn.microsoft.com/en-us/entra/agent-id/integrate-aws-bedrock-agent) \(New\) - Step-by-step guide for securing Bedrock agents with Agent ID.
- [Secure an n8n agent](https://learn.microsoft.com/en-us/entra/agent-id/integrate-n8n-agent) \(New\) - Deploy n8n on Azure with Agent ID integration.
- [Migrate custom app registrations](https://learn.microsoft.com/en-us/entra/agent-id/migrate-custom-app-registrations-to-agent-id) \(New\) - Move agents using standard app registrations to Agent ID.
- [Migrate Copilot Studio agents](https://learn.microsoft.com/en-us/entra/agent-id/migrate-copilot-studio-agents-to-agent-id) \(New\) - Move Microsoft Copilot Studio agents to Agent ID.

To simplify agent management across the enterprise, agent registry experiences are converging under [Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-registry). This change gives customers one place to discover and manage all agents, while Microsoft Entra continues to provide the identity foundation through Agent ID. For more information, see [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

## Govern agent identities and lifecycle

Microsoft Entra ID Governance extends lifecycle and access management capabilities to agent identities:

- [Governing agent identities overview](https://learn.microsoft.com/en-us/entra/id-governance/agent-id-governance-overview) - Overview of how Microsoft Entra governs agent identity lifecycle and access.
- [Access packages for agent identities](https://learn.microsoft.com/en-us/entra/agent-id/agent-access-packages) - Govern agent access through policy-based access packages and permission assignment for both on-behalf-of \(OBO\) and autonomous \(non-OBO\) scenarios.
- [Sponsor lifecycle workflows](https://learn.microsoft.com/en-us/entra/id-governance/agent-sponsor-tasks) \(New\) - Automate sponsor maintenance and reassignment for agent blueprints and agent identities.
- [Manage your agent identities](https://learn.microsoft.com/en-us/entra/agent-id/manage-agent-identities-end-user) \(New\) - View and control agent identities you own or sponsor.
- [Agent identity sponsor templates](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-templates) \(New\) - Two new lifecycle workflow templates for notifying managers and cosponsors, and automatically transfer sponsorship when an agent identity sponsor changes roles or leaves the organization, to prevent orphaned agents.

## Protect agent access to resources

Conditional Access and ID Protection features extend Microsoft Entra Agent ID to help secure agent identities and their access to resources:

- [Conditional Access for agents](https://learn.microsoft.com/en-us/entra/identity/conditional-access/agent-id) \(Updated\)- Improved guidance and detailed scenarios for Conditional Access policies, plus new templates for agent-specific policies.
- [Block access for high-risk agent identities](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-agent-block-high-risk) \(New\) - Conditional Access template to block sign-ins from risky agent identities.
- [Autonomous agent access policy](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-autonomous-agents) \(New\) - Conditional Access template for autonomous agents without user context.
- [On behalf of agent access policy](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-on-behalf-of-agents) \(New\) - Conditional Access template for agents acting on behalf of users.

## Related content

- [Security for AI overview](https://learn.microsoft.com/en-us/entra/agent-id/security-for-ai-overview)
- [Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/overview)
- [FAQ](https://learn.microsoft.com/en-us/entra/agent-id/faq)
