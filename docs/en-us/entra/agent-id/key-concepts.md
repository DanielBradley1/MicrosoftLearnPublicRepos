<!-- Source: https://learn.microsoft.com/en-us/entra/agent-id/key-concepts -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Microsoft Entra Agent ID key concepts

The Microsoft agent identity platform provides specialized identity constructs designed specifically for AI agents operating in enterprise environments. These identity constructs enable secure authentication and authorization patterns that differ from traditional user and application identities, addressing the unique requirements of autonomous AI systems.

This article explains the core concepts that form the foundation of agent identity management: agent identities, agent identity blueprints, and their supporting components. Understanding these concepts is essential for developers who need to implement secure, scalable authentication patterns for AI agents.

The agent identity architecture follows a hierarchical model where agent identity blueprints serve as templates for creating multiple agent instances, each with distinct identities and capabilities. This approach enables centralized management while providing the flexibility needed for diverse AI agent deployment scenarios.

## Core identity concepts

The following concepts form the foundation of Microsoft Entra Agent ID and the Microsoft agent identity platform.

### Agent identity

An agent identity is the primary identity an AI agent uses to authenticate to systems and access resources. Unlike user accounts, agent identities don't have credentials of their own. They authenticate using tokens issued by their agent identity blueprint. For more information, see [Agent identities](https://learn.microsoft.com/en-us/entra/agent-id/agent-identities).

### Agent identity blueprint

An agent identity blueprint is an object in Microsoft Entra ID that serves as the template and authentication foundation for one or more agent identities. The blueprint holds credentials and uses them to acquire tokens on behalf of all agent identities created from it. Policies and settings applied to a blueprint, such as Conditional Access, take effect for all its agent identities. For more information, see [Agent identity blueprints](https://learn.microsoft.com/en-us/entra/agent-id/agent-blueprint).

### Agent identity blueprint principal

When a blueprint is added to a tenant, Microsoft Entra creates a corresponding principal object. An agent identity blueprint principal is the Microsoft Entra object that records a blueprint's presence in a tenant and enables it to acquire tokens and appear in audit logs. For more information, see [Agent identity blueprint principals](https://learn.microsoft.com/en-us/entra/agent-id/agent-blueprint#agent-identity-blueprint-principals).

### Traditional service principal \(not recommended for AI agents\)

Traditional service principals were designed for static, deterministic workloads. Microsoft Entra Agent ID exists because service principals lack the governance infrastructure AI agents need. There's no enforced sponsorship, no agent-aware audit entries, and no blueprint-managed lifecycle. For more information, see [Agent identities, service principals, and applications](https://learn.microsoft.com/en-us/entra/agent-id/agent-service-principals).

### Regular user account \(not recommended for AI agents\)

Regular Microsoft Entra user accounts are designed for human sign-in patterns. Assigning them to AI agents causes failures across every Zero Trust enforcement layer: Conditional Access policies built for humans don't apply correctly to agents, ID Protection detections are degraded, and identity governance processes can incorrectly remove agent access. For more information, see [Plan your agent identity architecture](https://learn.microsoft.com/en-us/entra/agent-id/how-to-plan-agent-identity-architecture).

## Agent operation patterns

The agent identity platform supports the following patterns for how agents operate and authenticate, each serving different use cases and security requirements.

### Interactive agents

Interactive agents perform specific tasks on demand on behalf of a signed-in user, often through a chat interface. Tasks include analyzing customer data for sales recommendations or answering support questions with escalation to human representatives. These agents are granted Microsoft Entra delegated permissions that allow them to act on behalf of users using the on-behalf-of \(OBO\) authentication flow. Common scenarios include customer support assistants, research helpers, and real-time collaboration agents.

### Autonomous agents

Autonomous agents operate independently using their own identity, not a human user's identity. These agents run in the background, making decisions and taking actions without human intervention, such as monitoring network logs for security operations, managing infrastructure deployments with autoscaling, or processing scheduled maintenance tasks. Autonomous agents authenticate directly with the Microsoft Entra ID platform using their agent identity and the client credentials flow.

### Agent's user account

An agent's user account is an optional account that pairs 1:1 with an agent identity. It functions with human user characteristics, including persistent identities and access to organizational resources such as mailboxes, calendars, Teams channels, and documents. Use an agent's user account only when the agent must access systems that require a user object. An agent's user account doesn't replace the agent identity — both must exist. For more information, see [Agent's user accounts](https://learn.microsoft.com/en-us/entra/agent-id/agent-users).

## Agent owners, sponsors, and managers

The agent identity platform introduces an administrative model that separates technical administration from business accountability, ensuring operational control and compliance oversight without excessive permissions. The agent administrative roles include owners, managers, and sponsors.

- **Owners** serve as technical administrators for agents, handling operational and configuration aspects.
- **Sponsors** provide business accountability for agents, making lifecycle decisions without technical administrative access.
- **Managers** are human users who are designated as the hiring manager or operational owner for an agent's user account.

For more information, see [Administrative relationships for agent identities \(Owners, sponsors, and managers\)](https://learn.microsoft.com/en-us/entra/agent-id/agent-owners-sponsors-managers)

## Microsoft Entra ID Auth SDK \(sidecar\)

The Microsoft Entra ID Auth SDK \(sidecar\) is a containerized web service that handles token acquisition, validation, and secure downstream API calls for agents registered in the Microsoft identity platform. It runs as a companion container alongside your application, allowing you to offload identity logic to a dedicated service. For more information, see [Microsoft Entra ID Auth SDK \(sidecar\)](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/overview).

## Related content

- [What is an agent ID?](https://learn.microsoft.com/en-us/entra/agent-id/what-are-agent-identities)
- [Microsoft Entra Agent ID OAuth protocols](https://learn.microsoft.com/en-us/entra/agent-id/agent-oauth-protocols)
- [Inheritable permissions](https://learn.microsoft.com/en-us/entra/agent-id/concept-inheritable-permissions)
