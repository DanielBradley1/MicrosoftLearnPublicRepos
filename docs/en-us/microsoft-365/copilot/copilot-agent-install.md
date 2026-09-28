<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-agent-install -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Agent installation in Microsoft Copilot

Microsoft Copilot can be extended by installing agents. [Agents](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-overview) provide additional knowledge, skills, and automated workflows to address your unique business needs and enhance workflows within Microsoft Copilot. In addition, Microsoft Copilot can deliver highly skilled expertise on demand.

Note

Microsoft deployed [Researcher](https://go.microsoft.com/fwlink/?linkid=2329838) and [Analyst](https://go.microsoft.com/fwlink/?linkid=2329729) to existing users with Microsoft Copilot licenses.

There are different methods used to install agents in Microsoft Copilot.

## Agent installation and governance methods

Microsoft Copilot currently provides the following deployment and governance methods for agents:

- [Microsoft-installed agents and features](#microsoft-installed-agents-and-features)
- [Admin-installed agents](#admin-installed-agents)
- [User-installed agents](#user-installed-agents)

### Microsoft-installed agents and features

Microsoft may install a small number of agents and features that augment Microsoft Copilot with highly valuable skills. These agents and features, built by Microsoft, are preinstalled and/or pre-pinned in Microsoft Copilot for all licensed users. Currently, only Researcher and Analyst are deployed this way.

Organizations can govern agents in the Microsoft 365 admin center. There, administrators can block agents in their tenant, making them inaccessible to all users. Granular controls allowing assignment of these agents to specific users and groups are therefore grayed-out. Alternately, administrators can [disable or restrict Copilot extensibility](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps) for their organization, however this will apply to non-Microsoft deployed agents, as well as Microsoft-deployed agents. Individual users can share and unpin these agents as well.

### Admin-installed agents

Administrators can install their own custom-built, Microsoft-built, or partner-built agents to augment Microsoft Copilot. Administrators can install a limited number of agents to the Copilot rail or make them available to users through the [Agent Store in Microsoft Copilot](https://devblogs.microsoft.com/microsoft365dev/introducing-the-agent-store-build-publish-and-discover-agents-in-microsoft-365-copilot/).

Organizations can govern these agents in the Microsoft 365 admin center. Administrators have a full set of lifecycle management tools for these agents. Microsoft offers granular controls that enable administrators to install, block, and remove these agents for some or all of the users in their tenant.

Note

Admins can only remove shared agents and custom LOB agents.

For more information, see [Manage agents for Microsoft Copilot in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).

### User-installed agents

Users can install agents that are available in Agent Store based on the policies set by their tenant administrators. Users can also install their own custom-built agents. For example, these custom-built agents could be built with Microsoft SharePoint, Agent Builder in Microsoft Copilot, or Copilot Studio, to augment Microsoft Copilot. These agents are used by individuals, and optionally shareable within the user's organization.

Organizations can govern these agents in the Microsoft 365 admin center. Administrators have a full set of lifecycle management tools for these agents. Microsoft offers granular controls that enable administrators to install and block agents. Additionally, administrators can remove shared and custom agents for some or all of the users in their tenant.

### Microsoft-built agent licensing

Some agents built by Microsoft, including Researcher and Analyst, are governed by [Supplementary Terms of Service](https://support.microsoft.com/office/supplementary-terms-of-service-for-teams-apps-powered-by-microsoft-365-services-and-applications-bc6027fe-68c3-4758-a70d-cfe97c43b4e2) which refers to the Microsoft 365 [Product Terms](https://www.microsoft.com/licensing/terms/productoffering/Microsoft365/all), and by reference, includes the Data Protection Addendum \(DPA\). The same Product Terms and DPA also govern the Microsoft Copilot service.

## Related content

- [Agent management in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-365-overview)
- [Agent Store in Microsoft Copilot](https://devblogs.microsoft.com/microsoft365dev/introducing-the-agent-store-build-publish-and-discover-agents-in-microsoft-365-copilot/)
- [Agents for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-overview)
- [Build agents with Copilot Studio](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-build)
- [Copilot Studio overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-what-is-copilot-studio)
- [Overview of Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/overview)
- [Microsoft Agent 365 documentation](https://learn.microsoft.com/en-us/microsoft-agent-365/)
