<!-- Source: https://learn.microsoft.com/en-us/intune/copilot/agents/change-review-agent -->
<!-- Sitemap-Last-Modified: 2026-08-19 -->

# Change Review Agent overview

Important

**Starting August 31, 2026, the Policy Configuration Agent \(PCA\) and Change Review Agent \(CRA\) will no longer be available in the Microsoft Intune admin center.**

Review any existing processes that use these agents and complete any active agent runs before this date. Avoid creating new dependencies on these agents.

**What this change means for you**:

- You can continue using existing Policy Configuration Agent \(PCA\) and Change Review Agent \(CRA\) experiences until August 31, 2026.
- After August 31, 2026, these agents and their associated experiences are no longer accessible in the Microsoft Intune admin center.
- If your organization relies on these agents, review and update affected operational processes before the retirement date.

**Recommended actions**:

- Complete any active Policy Configuration Agent \(PCA\) and Change Review Agent \(CRA\) activities before **August 31, 2026.**
- Avoid creating new workflows or dependencies that rely on these agents.
- Review existing administrative processes that depend on these agents and plan alternative approaches before the retirement date

In public preview, the Microsoft Intune Change Review Agent uses Microsoft Security Copilot's generative AI to evaluate Multi Admin Approval requests for PowerShell scripts on Windows devices. It provides risk-based recommendations and contextual insights to help administrators understand script behavior and associated risks. These insights help Intune administrators make informed decisions more quickly about whether to approve or deny requests.

To generate these recommendations, the agent aggregates signals from multiple sources:

- Microsoft Defender Vulnerability Management - for threat insights
- Microsoft -Entra ID - for identity risk
- Microsoft Intune - for Multi Admin Approval requests and historical context of similar requests

The agent analyzes these signals to assess the potential risk associated with each request and then delivers actionable insights to support secure and efficient change management.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/cloud.svg) **Cloud requirements**

> The agent is supported on the public cloud only. It isn't supported on government clouds.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> To use Security Copilot agents in Microsoft Intune, your organization must meet specific licensing requirements.
> 
> Required licenses:
> 
> - [Microsoft Intune Plan 1 subscription](https://learn.microsoft.com/en-us/intune/fundamentals/licensing)
> - [Microsoft Entra ID P2](https://learn.microsoft.com/en-us/entra/fundamentals/licensing)
> - [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-prerequisites)
> - [Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/get-started-security-copilot) with sufficient security compute units \(SCUs\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/plugin.svg) **Plugins requirements**

> Plugins enable Security Copilot agents to connect with Microsoft services and perform specialized actions.
> 
> The Change Review Agent requires the following plugins:
> 
> - ![](https://learn.microsoft.com/en-us/intune/media/icons/16/intune.svg) [Microsoft Intune](https://learn.microsoft.com/en-us/intune/copilot/security-copilot)
> - ![](https://learn.microsoft.com/en-us/intune/media/icons/16/entra.svg) [Microsoft Entra](https://learn.microsoft.com/en-us/entra/fundamentals/copilot-security-entra)
> - ![](https://learn.microsoft.com/en-us/intune/media/icons/16/defender.svg) [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management)
> - ![](https://learn.microsoft.com/en-us/intune/media/icons/16/defender.svg) [Microsoft Threat Intelligence](https://learn.microsoft.com/en-us/defender/threat-intelligence/what-is-microsoft-defender-threat-intelligence-defender-ti)
> 
> [Learn more about plugins](https://go.microsoft.com/fwlink/?linkid=2316474).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Platform requirements and scenarios**

> The agent supports evaluation and recommendations for the following platforms and scenarios:
> 
> - Windows
> - PowerShell scripts in Intune

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> Role requirements vary based on whether you're configuring the agent or using it, and on the specific actions performed.
> 
> \---
> 
> To **enable and configure** the Change Review Agent, use an account with the following roles:
> 
> ![](https://learn.microsoft.com/en-us/intune/media/icons/16/entra.svg) Entra roles:
> 
> - [*Intune Administrator*](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)
> - [*Security Reader*](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-reader)
> - *Entra/Identity risky user \(read\)* - This permission maps to the Unified RBAC permission *Security posture / Identity risk / Risky users \(read\)*.
> 
> ![](https://learn.microsoft.com/en-us/intune/media/icons/16/defender.svg) Defender roles - Defender role-based access control \(RBAC\) roles depend on your Defender XDR implementation:
> 
> - [*Unified RBAC*](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac): Assign the Microsoft Entra ID Security Reader to the agent's identity account. This role provides read-only access to Defender Vulnerability Management data and automatically enforces device group scoping.
> - [*Granular RBAC*](https://learn.microsoft.com/en-us/defender-endpoint/rbac): Assign a custom RBAC role with permissions equivalent to the Unified RBAC Security Reader role. For example:
> 
>   - *View data – Defender Vulnerability Management* - This permission maps to the Unified RBAC permission *Security posture / Posture management / Vulnerability management \(read\)*.
> 
> 
>   For details about mapping permissions to the Unified RBAC Security Reader role, see [Microsoft Entra Global roles access](https://learn.microsoft.com/en-us/defender-xdr/compare-rbac-roles#microsoft-entra-global-roles-access) in the *Map Microsoft Defender XDR Unified role-based access control \(RBAC\)* article in the Defender documentation.
> 
> 
>   Ensure the agent's identity is scoped in Microsoft Defender to include all relevant device groups. The agent can't access or report on devices outside its assigned scope.
> 
> ![](https://learn.microsoft.com/en-us/intune/media/icons/16/copilot.svg) Security Copilot roles:
> 
> - [Copilot owner](https://learn.microsoft.com/en-us/copilot/security/authentication#security-copilot-roles)
> 
> \---
> 
> To **use** the agent, sign in with an account that has the following roles:
> 
> ![](https://learn.microsoft.com/en-us/intune/media/icons/16/intune.svg) Intune roles:
> 
> - [Read Only Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview#built-in-roles) or [custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview#custom-roles) with equivalent permissions.
> 
> ![](https://learn.microsoft.com/en-us/intune/media/icons/16/entra.svg) Entra roles:
> 
> - [Security Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-reader)
> 
> ![](https://learn.microsoft.com/en-us/intune/media/icons/16/defender.svg) Defender roles
> 
> - Use of the agent requires the same access as *enabling and configuring* the agent.
> 
> ![](https://learn.microsoft.com/en-us/intune/media/icons/16/copilot.svg) Security Copilot roles:
> 
> - [Copilot contributor](https://learn.microsoft.com/en-us/copilot/security/authentication#security-copilot-roles)

## How the agent works

The Change Review Agent operates using an Intune admins account identity and runs manually when an admin starts it.

At a high level, the agent does the following steps each time it runs:

1. **Signal aggregation** - The agent begins by aggregating signals from the following sources:

   - Microsoft Defender Vulnerability Management - for threat insights
   - Microsoft Entra ID - for identity risk
   - Microsoft Intune - for Multi Admin Approval requests and historical context of similar requests

2. **Evaluation** - The agent evaluates Windows PowerShell scripts for Multi Admin Approval requests using predefined logic that's built in to the agent configuration.
3. **Recommendations** - The agent reviews and then provides recommendations for a maximum of 10 requests per run.

   Suggestions are *suggestions* only. The approval or rejection of a request remains with an Intune administrator.

   The first column of the recommendation list presents Suggested Next Steps, which display the recommended action followed by the name of the request. Possible actions include:

   - Approve - Low-risk request; likely safe to approve.
   - Reject - High-risk request; shouldn't be approved.
   - Needs more info - Risk couldn't be fully assessed. This request requires further review.


   Each recommendation includes supporting details that explain:


   - The rationale behind the agent's recommendation.
   - What the script is intended to accomplish or do.
   - A detailed list of factors that the agent reviewed as part of its process.

## Agent identity

The agent runs under the identity and permissions of the Intune admin account used during setup. The agent's actions are limited to the permissions of that account, and the identity refreshes with each run. If the agent doesn't run for 90 consecutive days, its authentication expires, and subsequent runs fail until its renewed. To maintain functionality, renew the agent identity before the 90-day limit.

## Operational considerations

Before setting up and starting the agent for the first time, review the following considerations:

- An admin must manually start the agent. Once started, there's no option to stop or pause it.
- The agent can only be started from the Microsoft Intune admin center.
- Session details in the [Microsoft Security Copilot portal](https://go.microsoft.com/fwlink/?linkid=2247989) are visible only to the user who set up the agent.
- The agent reviews and then provides recommendations for a maximum of 10 requests per run.
- Only one agent instance is supported per tenant/user context.

## Set up the agent

The agent operates under the identity and permissions of the Intune admin account used during setup. Its operations are limited to the permissions of that account, and the identity refreshes with each run. Any changes to the account's permissions affect the agent's capabilities during its next run.

**To set up the Change Review Agent:**

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Agents** > **Change Review Agent**.
2. In **Overview**, select **Set up Agent** to open the *Set up Change review agent* pane.
3. The **Set up Change review agent** pane lists the required permissions and provides details about setup requirements. When requirements are met, select **Start agent**.

   ![Screenshot of the Set up Change review agent pane.](https://learn.microsoft.com/en-us/intune/copilot/agents/media/change-review-agent/setup.png)

The agent operates until it completes its evaluation and displays results in the Overview tab. When the run finishes, the agent is ready to use.

To learn more about using the agent, see [Use the Change Review Agent](https://learn.microsoft.com/en-us/intune/copilot/agents/manage-change-review-agent).

## Remove the agent

When you remove an agent, all associated data generated including suggestions and activities are deleted. Previously applied suggestions remain unchanged.

Steps to remove an agent instance:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents**.
2. Select the agent instance you want to remove.
3. Select **Remove agent** and confirm the removal.

After removal:

- The agent pane returns to its original state.
- An admin can reinstall the agent later by repeating the setup process.

## ![](https://learn.microsoft.com/en-us/intune/media/icons/32/feedback.svg) Help shape the future of Intune agents

Join our **Intune Agents Feedback Forum** to share insights and influence upcoming capabilities in Microsoft Intune.

Sign up and learn more: [https://aka.ms/IntuneAgentsForum](https://aka.ms/IntuneAgentsForum)

## Related content

- [Use the Change Review Agent](https://learn.microsoft.com/en-us/intune/copilot/agents/manage-change-review-agent)
