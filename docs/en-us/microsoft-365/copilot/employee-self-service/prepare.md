<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prepare -->
<!-- Sitemap-Last-Modified: 2026-05-22 -->

# Prepare to deploy the Employee Self-Service agent

Preparation is the first step to deploying the Employee Self-Service agent. You need to meet the [prerequisites](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prerequisites). The following roles are required to prepare the agent for deployment.

| Role | Activities to perform | Configuration areas |
| --- | --- | --- |
| Global admin | Assign the Power Platform Administrator role. | Microsoft admin center |
| Power Platform Administrator | Assign the Environment Maker role. | Power Platform admin center |
| Environment Maker | Create environments required for customizing and testing the Employee Self-Service agent. | Power Platform admin center and Microsoft Copilot Studio |
| InfoSec/IT Infrastructure/Change control board | Configure infrastructure requirements for external systems integration. | Network firewall policies and single sign-on |

## Power Platform environment strategy for the Employee Self-Service agent

The Employee Self-Service agent starters are tailored to each vertical, such as HR or IT, and each starter comes with its own unique set of topics and connectors. While it may be necessary to use separate Power Platform environments for better governance, if you want to link these vertical-specific agent starters to a single, central agent, we advise you to keep all the vertical agent starters within one Power Platform environment.

## Assign the Power Platform administrator role

1. Sign in as a Global admin to your [admin center](https://admin.microsoft.com).
2. Select **Roles**, then choose **Role assignments**.
3. In the **Microsoft Entra ID** section, find the **Power Platform Administrator** role.
4. Add identified users in the **Assigned** section.

## Set up your Power Platform environment

- To learn more about managed environments, refer to this [Power Platform article](https://learn.microsoft.com/en-us/power-platform/admin/managed-environment-overview) about managed environments.
- To learn more about creating a new Power Platform, refer to this [Power Platform article](https://learn.microsoft.com/en-us/power-platform/admin/create-environment?tabs=new) about environment creation.
- To create an environment with a Dataverse database, refer to these [Power Platform instructions](https://learn.microsoft.com/en-us/power-platform/admin/create-environment?tabs=new%22%20%5Cl%20%22create-an-environment-with-a-database).

## Assign the Environment Maker role

- To assign a security role to a user, refer to these [Power Platform instructions](https://learn.microsoft.com/en-us/power-platform/admin/assign-security-roles?tabs=new).
- To understand the role-permissions model, refer to these [Power Platform instructions](https://learn.microsoft.com/en-us/power-platform/admin/security-roles-privileges?tabs=new).

Note

Environment Makers can't install new agents. Only the environment administrators can install new agents.

Important

Important: Familiarize yourself with the Power Platform subscription plans and billing policies for your tenant. We recommend you perform initial [capacity planning](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/prerequisites#capacity-planning) before enabling and configuring the Employee Self-Service agent to make sure you don't incur additional billing.

Caution

Environments created with the Dataverse Database have the **System Administrator** role. This role has full permission to customize or administer the environment, including creating, modifying, and assigning security roles. This role can view all data in the environment. This built-in role can't be modified.

## Allow the external systems connector within Power Platform

Most enterprise organizations have Data Loss Prevention \(DLP\) policies setup for maintaining security and compliance within their Power Platform ecosystem. The connectors that need to be used with the Employee Self-Service agent must be allowed within Power Platform for the connector to be available for customization.

Work with your enterprise information security and/or Power Platform administrators to allowlist the connectors to be used with the Employee Self-Service agent.

### Required connectors

The following connectors must be allowed in your Power Platform DLP policy for the Employee Self-Service agent to deploy and operate. If any of these connectors are blocked by DLP, deployment or runtime configuration of the agent fails.

| System or scenario | Connector |
| --- | --- |
| ServiceNow Knowledge \(Microsoft Copilot connector\) | [ServiceNow Knowledge Microsoft Copilot connector overview](https://learn.microsoft.com/en-us/microsoftsearch/servicenow-knowledge-overview) |
| ServiceNow ITSM and HRSD | [ServiceNow connector](https://learn.microsoft.com/en-us/connectors/service-now/) |
| Workday | [Workday SOAP connector](https://learn.microsoft.com/en-us/connectors/workdaysoap/) |
| SAP SuccessFactors | [SAP OData connector](https://learn.microsoft.com/en-us/connectors/sapodata/) |
| Microsoft Dataverse | [Microsoft Dataverse connector](https://learn.microsoft.com/en-us/connectors/commondataserviceforapps/) |
| Microsoft 365 Self-Help \(Alchemy\) | [Microsoft 365 Self-Help connector](https://learn.microsoft.com/en-us/connectors/alchemy/) |
| User profile lookups \(required by built-in topics and flows\) | [Office 365 Users connector](https://learn.microsoft.com/en-us/connectors/office365users/) |

Note

Only allow the connectors for the source systems your deployment actually uses. The Office 365 Users connector is required for all Employee Self-Service deployments because built-in topics and flows look up the signed-in user's profile.

## Infrastructure setup for external systems integration

Most organizations secure their third-party HR systems and knowledge sources from external networks to protect sensitive information about employees, organizations, knowledge assets, and other data.

You need to make these systems accessible to the Power Platform environment where the Employee Self-Service agent is hosted in order to integrate them into the agent.

These systems must be configured with allowlists for the source IP addresses from the Power Platform environment where the Employee Self-Service agent is hosted and executed.

[Learn about Power Platform URLs and IP address ranges](https://learn.microsoft.com/en-us/power-platform/admin/online-requirements).

[Learn about Managed connectors outbound IP addresses](https://learn.microsoft.com/en-us/connectors/common/outbound-ip-addresses#power-platform).

Tip

Before you mark this preparation stage complete, [run FlightCheck](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/commands-reference#flightcheck-readiness-check) to proactively validate that DLP policies, connector allowlists, IP allowlists, and environment settings meet the agent's requirements.

## Preparation checklist

Use the following checklist to make sure you're ready to move on to the next stage of deployment. If any of these checks fail, you need to repeat the steps in this article.

| Role | Verification steps | Result |
| --- | --- | --- |
| Environment administrator | 1. Sign into the Power Platform admin center.  <br>2. Select Environments to confirm your newly created environment is listed.  <br>3. Confirm the following settings for your new environment: Dataverse= yes, release cycle = standard. | Pass/Fail |
| Environment administrator | Confirm agents can be installed from Copilot Studio. | Pass/Fail |
| Environment maker | Access your newly created environment from Copilot Studio. | Pass/Fail |
