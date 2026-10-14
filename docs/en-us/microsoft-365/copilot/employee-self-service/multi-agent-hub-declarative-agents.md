<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/multi-agent-hub-declarative-agents -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Set up the Employee Self-Service hub for declarative agents

The Employee Self-Service hub gives employees one place to get help across multiple business domains. This article explains how to build the hub by connecting Employee Self-Service declarative agents. Each connected agent focuses on a specific domain and provides specialized capabilities, while the hub routes employee requests to the appropriate agent.

This approach provides a consistent employee experience while allowing makers to build, manage, and improve each domain agent independently.

Note

We recommend you start by installing and configuring your domain agents, such as Employee Self-Service HR and Employee Self-Service IT, before setting up the hub agent.

## Set up the Employee Self-Service Agent hub

### Prerequisites

Before you set up the Employee Self-Service Agent hub, publish the declarative agents that you want to connect. These agents can include the Employee Self-Service HR and Employee Self-Service IT agents. The hub can also connect to other published declarative agents.

### Install the hub agent

Install the Employee Self-Service Agent hub. The hub agent includes out-of-the-box instructions for routing requests to connected agents.

### Connect domain agents to the hub

The Employee Self-Service Agent hub uses the connected agents feature. You can connect the Employee Self-Service HR and Employee Self-Service IT agents or any other published declarative agent.

1. Open the hub agent.
2. On the **Configure** tab, select **Agents**.
3. Add the declarative agents that you want the hub to use.
4. Make sure each connected agent has a clear description. The hub uses these descriptions to make orchestration and routing decisions.

Note

You can connect up to 10 domain agents to the hub agent.

### Publish the hub agent

Follow your standard application lifecycle management \(ALM\) practices to publish and deploy the hub agent.

Note

After you publish the hub agent, direct employees to use it as their entry point for Employee Self-Service instead of going directly to the individual domain agents.

### Validate in Microsoft Copilot Chat

1. Open Microsoft Copilot Chat and find the Employee Self-Service Agent.
2. Validate scenarios from each connected domain from start to finish.
3. Confirm that the hub routes each request to the appropriate connected agent and returns the expected response.
