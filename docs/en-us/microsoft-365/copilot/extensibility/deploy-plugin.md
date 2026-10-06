<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/deploy-plugin -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Make plugins and agents available

Use this page if you administer the organization receiving the plugin or agent. Start from the publishing record supplied by the publisher, then complete only the actions required by that distribution route.

You enter this stage with the exact publishing record and an identified owner or administrator for the next action.

Some supported direct-sharing routes are completed by the owner and intended users without an administrator. Don't treat development sideloading or direct sharing as a substitute for a production route that requires organizational review or assignment.

Note

Administrators who need an end-to-end lifecycle map should begin with [Administer Microsoft 365 Copilot plugins and agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/administrator-guide).

## Before you begin

Have:

- The exact identity and version that was published or shared.
- The publisher or creator identity and any publisher provenance supplied by the route.
- The publishing route and its submission, offer, or org catalog identifier.
- The intended users or groups and target Microsoft 365 experiences.
- Included agents, skills, connectors, MCP servers, and other components, including their descriptions and dependencies.
- Required licenses, permissions, consent, connections, and external services.
- An owner for support, updates, and removal.

## Follow the distribution route

### Direct and personal sharing

- For an Agent Builder agent, the owner follows [Share and manage agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-share-manage-agents#share-an-agent).
- For a declarative agent or alpha plugin package shared with WIQD, the owner follows the applicable `wiqd agent share` or `wiqd plugin share` procedure and confirms the intended users or tenant can access it.
- For another supported direct-sharing route, follow the authoring experience's ownership, sharing, and access procedure.

Confirm that the intended users can access the shared solution and complete any required connections.

### Organizational catalog

- For a declarative agent published with `wiqd agent publish`, follow the [Work IQ Dev Tools agent lifecycle](https://microsoft.github.io/wiqd/concepts/agent-lifecycle/), then complete any required organizational-catalog actions.
- For an alpha WIQD plugin package uploaded as a custom app, follow the administration procedure for the resulting Microsoft 365 app package. The `wiqd plugin` surface doesn't publish to the org catalog.
- For an Agent Builder submission, follow [Submit agents from Agent Builder to your org catalog](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-submit-to-org-catalog) and [Manage agent requests](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-requests?context=/microsoft-365/copilot/extensibility/context).
- For an organizational submission from Microsoft 365 Agents Toolkit, Copilot Studio, or another supported app-package route, follow [Manage agent requests](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-requests?context=/microsoft-365/copilot/extensibility/context) or [Manage agents in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps?context=/microsoft-365/copilot/extensibility/context), as specified by the publishing procedure.

Review the submitted object, publish or approve it when required, and select who can install or access it.

### Public or Marketplace offering

Confirm the exact Microsoft Marketplace offer and package version. When the offer requires organizational acquisition or assignment, follow the administration procedure documented for the offer type, then [manage the agent in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps?context=/microsoft-365/copilot/extensibility/context) when applicable.

### Direct connector deployment

For a Copilot connector, follow [Deploy Copilot connectors](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/deployment-overview?context=/microsoft-365/copilot/extensibility/context) to create the connection, select users, configure content, and manage synchronization.

If the route isn't listed, follow the post-publishing procedure documented for its package type and authoring tool. Don't infer an approval, assignment, or enablement requirement from a different route.

## Complete the administrator actions

1. Review or acquire the exact artifact identified in the publishing record.
2. Approve the solution when required by the distribution route or organizational policy.
3. Assign the solution to the intended users or groups.
4. Enable it in each applicable Microsoft 365 experience.
5. Configure required connections, authentication, permissions, consent, and external services.
6. Verify that intended users can find, access, connect to, and use it in each supported experience.
7. Record the audience, verified experiences, completed actions, connections, owner, and date.

Installing a tool, assigning an agent, and configuring a connector are separate operations. Complete each operation that the solution requires.

## Record the availability result

Record:

- Intended users or groups.
- Enabled Microsoft 365 experiences.
- Completed reviews, approvals, acquisition, assignment, and enablement actions.
- Required connections, authentication, permissions, consent, and external services.
- Responsible owner or administrator.
- Verification date, tested users, and tested experiences.
- Known blockers, limitations, or follow-up actions.

You leave this stage with a verified availability record or a documented blocker and owner.

## If a required route or control isn't available

Stop and record the plugin or agent as blocked. Identify the missing route, permission, product capability, or owner. Don't substitute a sharing link or development sideload for a supported production route.

Return to [choose how to publish and distribute your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish) if the selected publishing route can't reach the intended audience.

Note

Administration experiences and interface labels can vary during the rollout. Follow the linked product documentation for the current procedure and interface.

## Next step

[Govern access, tools, and connections](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/manage)

## Related content

- [Make plugins and agents available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins)
- [Manage agent requests](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-requests?context=/microsoft-365/copilot/extensibility/context)
- [Manage tools for agents](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-tools-for-agent?context=/microsoft-365/copilot/extensibility/context)
- [For administrators](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/administrator-guide)
