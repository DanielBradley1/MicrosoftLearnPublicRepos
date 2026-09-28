<!-- Source: https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-autonomous-agents -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Recommended policies for autonomous agents

Use this guide to configure Conditional Access for agents that authenticate with their own identity, with no signed-in user. The access pattern is known **client credentials flow**. Instead of acting on behalf of a user, the agent authenticates with its own credentials - a client ID paired with a certificate or managed identity managed by the agent identity blueprint. This access pattern applies in the following scenarios:

- **Autonomous agents that operate independently**:

  - These agents run in the background, responding to events, or run on a schedule. A typical example is an agent that generates a daily report and sends the result to a group of employees. In this scenario, there is no user present, and the agent operates on its own.

- **Agents that don't always act on a user's behalf**:

  - Sometimes agents operate entirely on their own. For example, a backend SMS service that is not accessible to users. In this scenario, the OBO flow is not applicable and agent accesses the target resource by authenticating directly with its own identity.

- **Agents published on the web for public use**:

  - These agents either don’t authenticate the user or don’t support delegating the user’s context to downstream resources.

In those scenarios, the agent is the one who requests access, and the issued access token's subject is the [agent identity](https://learn.microsoft.com/en-us/entra/agent-id/what-are-agent-identities) rather than the user. As a result, the Conditional Access policy scope applies to the **agent identity**, not a user.

Important

Before configuring a Conditional Access policy, read the [Conditional Access for agents](https://learn.microsoft.com/en-us/entra/identity/conditional-access/agent-id) article. It covers the authentication flow, service boundaries, and limitations to ensure you cover all scenarios and your corporate data and services are well protected.

## Allow only specific agents to access resources

There are two key business scenarios where Conditional Access policies can help you manage agents effectively. In the first scenario you might want to ensure that only approved agents can access resources. You can do this by tagging agents and resources with [custom security attributes](https://learn.microsoft.com/en-us/entra/fundamentals/custom-security-attributes-overview) targeted in your policy, or by manually selecting them using the enhanced object picker.

- [Use the enhanced object picker](#tabpanel_1_use-the-enhanced-object-picker)
- [Use custom security attributes](#tabpanel_1_use-custom-security-attributes)

### Create Conditional Access policy using the enhanced object picker

Alternatively, organizations can create a Conditional Access policy using the enhanced object picker to block all agents except those reviewed and approved by your organization.

The enhanced object picker replaces the previous flat list experience in both the assignment and target resources sections of policy configuration. The new experience is meant to simplify the selection of items you want to scope in the policy.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**.
3. Select **New policy**.
4. Give your policy a name. Create a meaningful standard for the names of your policies.
5. Under **Assignments**, select **Users, agents or workload identities**.

   1. Under **What does this policy apply to?**, select **Agents**.

      1. Under **Include**, select **All agent identities**.
      2. Under **Exclude**:

         1. Select **Select individual agent identities**.
         2. Using the enhanced object picker, switch between the tabs **All**, **Agent blueprint principals**, and **Agent identities** to select the individual agent blueprints and/or agent identities approved for use in your environment.
         3. Select **Select**.

6. Under **Target resources**:

   1. Under **Include**, select **All resources \(formerly 'All cloud apps'\)**.

7. Under **Access controls** > **Grant**:

   1. Select **Block**.
   2. Select **Select**.

8. Confirm your settings and set **Enable policy** to **Report-only**.
9. Select **Create** to create your policy.

After confirming your settings using [policy impact or report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results), move the **Enable policy** toggle from **Report-only** to **On**.

### Create Conditional Access policy using custom security attributes

The recommended approach for the first scenario is to create and assign custom security attributes to each agent or agent blueprint, then target those attributes with a Conditional Access policy. This approach uses steps similar to those documented in [Filter for applications in Conditional Access policy](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-filter-for-applications). You can assign attributes across multiple attribute sets to an agent or cloud application.

#### Create and assign custom attributes

1. Create the custom security attributes:

   1. Create an **Attribute set** named *AgentAttributes*.
   2. Create **New attributes** named *AgentApprovalStatus* that **Allow multiple values to be assigned** and **Only allow predefined values to be assigned**.

      1. Add the following predefined values: **New**, **In\_Review**, **HR\_Approved**, **Finance\_Approved**, **IT\_Approved**.

2. Create another attribute set to group resources that your agents are allowed to access.

   1. Create an **Attribute set** named *ResourceAttributes*.
   2. Create **New attributes** named *Department* that **Allow multiple values to be assigned** and **Only allow predefined values to be assigned**.

      1. Add the following predefined values: **Finance**, **HR**, **IT**, **Marketing**, **Sales**.

3. Assign the appropriate value to resources that your agent is allowed to access. For example, you might want only agents that are **HR\_Approved** to be able to access resources that are tagged **HR**.

#### Create Conditional Access policy

After you complete the previous steps, create a Conditional Access policy using custom security attributes to block all agents except those reviewed and approved by your organization.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator) and [Attribute Assignment Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#attribute-assignment-reader).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**.
3. Select **New policy**.
4. Give your policy a name. Create a meaningful standard for the names of your policies.
5. Under **Assignments**, select **Users, agents or workload identities**.

   1. Under **What does this policy apply to?**, select **Agents**.

      1. Under **Include**, select **All agent identities**.
      2. Under **Exclude**:

         1. Select **Select agent identities based on attributes**.
         2. Set **Configure** to **Yes**.
         3. Select the Attribute we created earlier called **AgentApprovalStatus**.
         4. Set **Operator** to **Contains**.
         5. Set **Value** to **HR\_Approved**.
         6. Select **Done**.

6. Under **Target resources**:

   1. Under **Include**, select **All resources \(formerly 'All cloud apps'\)**.

7. Under **Access controls** > **Grant**:

   1. Select **Block**.
   2. Select **Select**.

8. Confirm your settings and set **Enable policy** to **Report-only**.
9. Select **Create** to create your policy.

After confirming your settings using [policy impact or report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results), move the **Enable policy** toggle from **Report-only** to **On**.

## Block high-risk agents from accessing organizational resources

In the second scenario, organizations can create a Conditional Access policy to block high-risk agents based on [signals from Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/concept-risky-agents). For details on risk detection types and response actions for agents, see [Identity Protection for agents](https://learn.microsoft.com/en-us/entra/id-protection/concept-risky-agents).

The following steps create a Conditional Access policy to block all high-risk agents from accessing your organization's resources.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**.
3. Select **New policy**.
4. Give your policy a name. Create a meaningful standard for the names of your policies.
5. Under **Assignments**, select **Users, agents or workload identities**.

   1. Under **What does this policy apply to?**, select **Agents**.

      1. Under **Include**, select **All agent identities**.

6. Under **Target resources**:

   1. Under **Include**, select **All resources \(formerly 'All cloud apps'\)**.

7. Under **Conditions** > **Agent risk \(Preview\)**, set **Configure** to **Yes**.

   1. Under **Configure agent risk levels needed for policy to be enforced**, select **High**. This guidance is based on Microsoft recommendations and might be different for each organization.

8. Under **Access controls** > **Grant**.

   1. Select **Block**.
   2. Select **Select**.

9. Confirm your settings and set **Enable policy** to **Report-only**.
10. Select **Create** to enable your policy.

After confirming your settings using [policy impact or report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results), move the **Enable policy** toggle from **Report-only** to **On**.

## Policies for autonomous agents' user accounts

Some autonomous agents can operate like users with their own mailboxes, group memberships, and enterprise identities. These agents use an [agent's user account](https://learn.microsoft.com/en-us/entra/agent-id/agent-users) instead of \(or in addition to\) an agent identity.

Conditional Access extends policy enforcement to these user-like autonomous agents. Administrators can:

- Target all agent users or select specific agent users
- Apply policies using custom security attributes
- Apply agent risk conditions to block risky agents
- Use the agent execution environments condition to scope policies to agents running on endpoints
- Enforce device compliance for agents running on managed endpoints \(Windows 365 Cloud PCs\)
- Enforce compliant network locations for agents with a Global Secure Access client

To create a Conditional Access policy for agents operating with their own identity, use the following settings:

- **Assignments**: In an agent access flow, the access token is issued to the agent identity \(the token subject\), so you assign the policy to agents or their agent identity blueprint.
- **Target resources**: Select the resources the agent needs to access.
- **Conditions**: Configure whether the agent is at risk. For more information, see [ID Protection for agents](https://learn.microsoft.com/en-us/entra/id-protection/concept-risky-agents).
- **Access control**: Because this agent accesses resources with its own identity, there's no remediation and the only available option is blocking access.

### Block risky agents' user accounts

This policy blocks autonomous agents operating as users when [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/concept-risky-agents) detects medium or high risk.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**.
3. Select **New policy**.
4. Give your policy a name. Create a meaningful standard for the names of your policies.
5. Under **Assignments**, select **Users, agents or workload identities**.

   1. Under **What does this policy apply to?**, select **Agents**.

      1. Under **Include**, select **All agent users \(Preview\)**.

6. Under **Target resources**:

   1. Under **Include**, select **All resources \(formerly 'All cloud apps'\)**.

7. Under **Conditions** > **Agent risk \(Preview\)**, set **Configure** to **Yes**.

   1. Under **Configure agent risk levels needed for policy to be enforced**, select **Medium** and **High**.

8. Under **Access controls** > **Grant**.

   1. Select **Block**.
   2. Select **Select**.

9. Confirm your settings and set **Enable policy** to **Report-only**.
10. Select **Create** to enable your policy.

### Require a compliant device for agents' user accounts

Some autonomous agents are computer-using agents. These agents operate a desktop environment to complete tasks, similar to how a human user interacts with applications. They typically run on dedicated [Windows 365 Cloud PCs for Agents](https://learn.microsoft.com/en-us/windows-365/agents/introduction-windows-365-for-agents), which are Intune-managed Windows devices. Because the Cloud PC is a managed endpoint, its compliance status can be evaluated by Conditional Access just like an employee's laptop.

However, not all agents run on endpoints. Agents running directly in Microsoft infrastructure don't have an associated device. Policies scoped with this condition don't apply to those cloud-native agents, which prevents unintended blocking.

The **Agent execution environments \(Preview\)** condition solves this by restricting the policy to only apply when the agent user session is initiated from an endpoint. Cloud-native agents without a device are excluded from evaluation entirely.

Note

An agent can technically run on any machine. But device compliance checks require Intune enrollment, which today is only supported on Windows 365 Cloud PCs for Agents. Without the **Agent execution environments** condition scoping this policy, agents running in cloud infrastructure are blocked with no path to compliance.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**.
3. Select **New policy**.
4. Give your policy a name. Create a meaningful standard for the names of your policies.
5. Under **Assignments**, select **Users, agents or workload identities**.

   1. Under **What does this policy apply to?**, select **Agents**.

      1. Under **Include**, select **All agent users \(Preview\)**.

6. Under **Target resources**:

   1. Under **Include**, select **All resources \(formerly 'All cloud apps'\)**.

7. Under **Conditions** > **Agent execution environments \(Preview\)**, set **Configure** to **Yes**.

   1. Under **Include**, select **Agent user sessions initiated from endpoints**.

8. Under **Access controls** > **Grant**.

   1. Select **Grant access**.
   2. Select **Require device to be marked as compliant**.
   3. Select **Select**.

9. Confirm your settings and set **Enable policy** to **Report-only**.
10. Select **Create** to enable your policy.

After confirming your settings using [policy impact or report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results), move the **Enable policy** toggle from **Report-only** to **On**.

### Require a compliant network for agents' user accounts

Similar to device compliance, you can require agents running on endpoints to connect through a compliant network using [Global Secure Access](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access). The Global Secure Access client installed on the endpoint provides the network location signal that Conditional Access evaluates.

Use the **Agent execution environments \(Preview\)** condition to scope this policy to endpoint-based sessions only. Without this condition, cloud-native agents without a Global Secure Access client are blocked with no path to compliance.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Conditional Access Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#conditional-access-administrator).
2. Browse to **Entra ID** > **Conditional Access** > **Policies**.
3. Select **New policy**.
4. Give your policy a name. Create a meaningful standard for the names of your policies.
5. Under **Assignments**, select **Users, agents or workload identities**.

   1. Under **What does this policy apply to?**, select **Agents**.

      1. Under **Include**, select **All agent users \(Preview\)**.

6. Under **Target resources**:

   1. Under **Include**, select **All resources \(formerly 'All cloud apps'\)**.

7. Under **Conditions** > **Agent execution environments \(Preview\)**, set **Configure** to **Yes**.

   1. Under **Include**, select **Agent user sessions initiated from endpoints**.

8. Under **Access controls** > **Grant**.

   1. Select **Grant access**.
   2. Select **Require compliant network**.
   3. Select **Select**.

9. Confirm your settings and set **Enable policy** to **Report-only**.
10. Select **Create** to enable your policy.

After confirming your settings using [policy impact or report-only mode](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-report-only#reviewing-results), move the **Enable policy** toggle from **Report-only** to **On**.

## Related content

- [Manage agent identities in your organization](https://learn.microsoft.com/en-us/entra/agent-id/manage-agent-identities-organization) - Overview of agent management across the full lifecycle.
- [Conditional Access for agents](https://learn.microsoft.com/en-us/entra/identity/conditional-access/agent-id)
- [Conditional Access template policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-policy-common)
- [Conditional Access: Users, groups, agents, and workload identities](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-users-groups)
- [Conditional Access: Target resources](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-cloud-apps)
- [Conditional Access: Conditions](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-conditions)
- [Conditional Access: Grant](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-grant)
- [Security for AI with Microsoft Entra agent identity](https://learn.microsoft.com/en-us/entra/agent-id/security-for-ai-overview)
- [Microsoft Entra ID Protection and agents](https://learn.microsoft.com/en-us/entra/id-protection/concept-risky-agents)
