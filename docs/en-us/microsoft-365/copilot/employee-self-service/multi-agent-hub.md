<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/multi-agent-hub -->
<!-- Sitemap-Last-Modified: 2026-05-29 -->

# Employee Self-Service Agent hub

The Employee Self-Service Agent hub gives employees a single front door for HR and IT help. You can set up one parent agent that routes queries to other domain agents through a seamless experience. This functionality is suited for teams that use multiple domain agents and require a unified agent experience.

## Set up the Employee Self-Service Agent hub

### Prerequisites

Before you set up the Employee Self-Service Agent, make sure you meet the following requirements:

- Complete the [installation](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/install) and [publishing](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/publish) steps for the Employee Self-Service HR and Employee Self-Service IT agents.
- Publish domain agents in a single Microsoft Copilot Studio environment.
- Verify you have the required [roles](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/deploy-overview-alm) assigned: Power Platform admin, Copilot Studio maker, or HR/IT application owner.

### Install the hub agent

Install the Employee Self-Service Agent in the Copilot Studio environment where your Employee Self-Service domain agents are already installed and published. The parent agent includes out-of-the-box instructions for routing to connected agents. Contact your Microsoft account team for access to the Employee Self-Service Agent.

### Connect domain agents to the parent

The Employee Self-Service Agent hub uses Copilot Studio Connected Agents, which aren't limited to the Employee Self-Service HR and Employee Self-Service IT agents. Any Copilot Studio agent published in the same environment can be connected as a child agent.

1. Open the parent agent in Copilot Studio.
2. Select **Overview** > **Agents**.
3. Add Employee Self-Service HR and Employee Self-Service IT as connected agents.
4. Provide clear descriptions for each connected agent. These descriptions inform the parent agent's orchestration and routing decisions.

Test the updated parent agent and its behavior with the connected agents before moving on to the next step.

### Publish the parent agent

1. [Publish](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/publish) the agent.
2. In the **Microsoft 365 admin center**, deploy the app to selected users for the initial rollout.

Tip

We recommend you start with a small group of pilot users who can test and provide feedback on the configurations.

### Validate in Microsoft Copilot Chat

1. Open Microsoft Copilot Chat and find the parent Employee Self-Service Agent.
2. Validate a mix of HR and IT scenarios end-to-end.
3. Confirm correct routing and responses.

## Other configurations

### Configure connected agents for personalized responses

For personalized responses in multi-agent setups, configure each connected agent:

1. Go to the connected agent configuration page.
2. Select **Open code view**.
3. Add `shouldSendStartConversation:true`.

Note

Welcome suppression is already updated in the Employee Self-Service HR and Employee Self-Service IT domain agents. To avoid double greetings when the parent agent does routing, update both agents to the latest version.
