<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentregistry?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# agentRegistry resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Represents the [Microsoft Entra Agent Registry](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform/what-is-agent-registry), which serves as a centralized repository for managing AI agents within an organization. The agent registry allows administrators to register, organize, and manage AI agents and their capabilities, including agent identities, agent users, and agent identity blueprints.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta)

## Methods

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| agentCardManifests | [agentCardManifest](https://learn.microsoft.com/en-us/graph/api/resources/agentcardmanifest?view=graph-rest-beta) collection | Represents the manifest definition for an AI agent. |
| agentCollections | [agentCollection](https://learn.microsoft.com/en-us/graph/api/resources/agentcollection?view=graph-rest-beta) collection | Represents a collection of agent instances. |
| agentInstances | [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) collection | Represents a specific deployed instance of an AI agent in the agent registry. |
