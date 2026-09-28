<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/governance-deployment-employee-lifecycle -->
<!-- Sitemap-Last-Modified: 2025-04-30 -->

# Microsoft Entra ID Governance deployment guide for employee lifecycle automation

Deployment scenarios are guidance on how to combine and test Microsoft Security products and services. You can discover how capabilities work together to improve productivity, strengthen security, and more easily meet compliance and regulatory requirements.

The following products and services appear in this guide:

- [Microsoft Entra ID Governance](https://learn.microsoft.com/en-us/entra/id-governance/identity-governance-overview)
- [Lifecycle workflows](https://learn.microsoft.com/en-us/entra/id-governance/what-are-lifecycle-workflows)
- [Microsoft Entra](https://learn.microsoft.com/en-us/entra/fundamentals/what-is-entra)
- [Microsoft Entra Connect](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-azure-ad-connect)
- [Microsoft Entra Cloud Sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)
- [Azure Logic Apps](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview)
- [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview)

Use this scenario to help determine the need for Microsoft Entra ID Governance to create and grant access for your organization. Learn how you can provision your users effectively, securely, and consistently with employee lifecycle automation.

## Timelines

Timelines show approximate delivery stage duration and are based on scenario complexity. Times are estimations and vary depending on the environment.

1. HR provisioning - 3 hours
2. Software-as-a-Service \(SaaS\) app provisioning - 1 hour
3. Lifecycle workflows - 3 hours

## Employee lifecycle automation

To streamline employee identity management, organizations are adopting modern solutions and automation. With identity management systems and technologies, IT staff can overcome limited manual procedures and instead enhance efficiency.

### Microsoft Entra ID Governance

With the Microsoft Entra ID Governance solution, organizations improve productivity, strengthen security, and meet compliance and regulatory requirements. Use Microsoft Entra ID Governance to ensure the right people have the right access to the right resources at the right time. Learn more about Microsoft Entra ID Governance [use cases](https://learn.microsoft.com/en-us/entra/id-governance/scenarios/identity-governance-use-cases) and [documentation](https://learn.microsoft.com/en-us/entra/id-governance/identity-governance-overview).

## HR-driven provisioning

HR-driven provisioning creates digital identities based on a human resources \(HR\) system, which becomes the source of authority. This juncture is the starting point for numerous provisioning processes.

Learn more in the video about [HR-driven provisioning with Microsoft Entra ID](https://youtu.be/HsdBt40xEHs).

### Cloud HR to Microsoft Entra ID

Users are created in Microsoft Entra ID, and other SaaS apps that support user provisioning. When employee records are updated in cloud HR, the user account is updated in Microsoft Entra ID and supporting SaaS apps.

## Deploy Workday to Microsoft Entra ID

1. [Select cloud HR provisioning connector apps](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/plan-cloud-hr-provision).
2. [Design provisioning topology](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/plan-cloud-hr-provision).
3. [Configure integration system user in Workday](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-inbound-tutorial).
4. [Enable Workday provisioning connector](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-inbound-cloud-only-tutorial).
5. [Start Workday and Microsoft Entra ID attribute mapping](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-inbound-cloud-only-tutorial).
6. [\(**Optional**\) Configure Workday writeback in Azure AD](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-writeback-tutorial).
7. [Enable and launch provisioning](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-writeback-tutorial).

Learn more in the video about [HR-driven user provisioning with Workday](https://youtu.be/TfndXBlhlII).

## Deploy SuccessFactors to Microsoft Entra ID

1. [Select cloud HR provisioning connector apps](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/plan-cloud-hr-provision).
2. [Design provisioning topology](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/plan-cloud-hr-provision).
3. [Create API user account in SuccessFactors](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-inbound-provisioning-cloud-only-tutorial).
4. [Create API permissions in SuccessFactors](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-inbound-provisioning-cloud-only-tutorial).
5. [Add SuccessFactors inbound connector app](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-inbound-provisioning-cloud-only-tutorial).
6. [Configure SuccessFactors attribute mappings](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-inbound-provisioning-cloud-only-tutorial).
7. [\(**Optional**\) Configure attribute write-back from Entra ID to SAP SuccessFactors](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-writeback-tutorial).
8. [Enable and Launch provisioning](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-writeback-tutorial).

Learn more in the video about [HR-driven user provisioning with SuccessFactors](https://www.youtube.com/watch?v=66v2FR2-QrY).

## Cloud HR to Active Directory

Use the following video to learn about API-driven inbound provisioning for on-premises Active Directory.  
  


<iframe src="https://learn-video.azurefd.net/vod/player?id=fa17234c-ecc7-4c87-82e9-6609270e1744" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Deploy Workday to Active Directory

1. [Select cloud HR provisioning connector apps](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/plan-cloud-hr-provision).
2. [Design provisioning topology](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/plan-cloud-hr-provision).
3. [Configure integration system user in Workday](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-inbound-tutorial).
4. [Provisioning connector app and Provisioning Agent](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-inbound-tutorial).
5. [Install and configure on-premises agents](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-inbound-tutorial).
6. [Configure connectivity to Workday and Active Directory](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-inbound-tutorial).
7. [Configure attribute mappings](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-inbound-tutorial).
8. [Enable and launch user provisioning](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-inbound-tutorial).

## Deploy SuccessFactors to Active Directory

1. [Select cloud HR provisioning connector apps](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/plan-cloud-hr-provision).
2. [Design provisioning topology](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/plan-cloud-hr-provision).
3. [Configure integration system user in Workday](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workday-inbound-tutorial).
4. [SuccessFactors inbound provisioning app and agent](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-inbound-provisioning-tutorial).
5. [Install on-premises agents](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-inbound-provisioning-tutorial).
6. [Configure app connectivity to AD](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-inbound-provisioning-tutorial).
7. [Configure attribute mappings](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-inbound-provisioning-tutorial).
8. [Enable and launch user provisioning](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/sap-successfactors-inbound-provisioning-tutorial).

## API-driven provisioning

Identity data in Microsoft Entra ID is kept in sync with workforce data managed in systems of record: an HR app, a payroll app, a spreadsheet, SQL tables in a database on-premises, or in the cloud. With application programming interface [\(API\)-driven inbound provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-concepts), the Microsoft Entra provisioning service supports integration with systems of record.

Learn more:

- [FAQ: API-driven inbound provisioning](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-faqs)
- [Grant access to the inbound provisioning API](https://youtu.be/RnY9T7k1BL0)
- [Learn to test provisioning API with Graph Explorer](https://youtu.be/GvEdWPgQJps)

### API-driven provisioning scenarios

IT teams import data extracts with automation. Independent software vendors \(ISVs\) integrate with Microsoft Entra ID. System integrators build connectors to systems of record. This process is commonly used for sources like flat files, CSV files, SQL staging tables. Integrate automation tools: [PowerShell](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/powershell) scripts, [Azure Logic Apps](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview), and workflows using HTTP calls.

## Configure API-driven provisioning

You can learn to configure [API-driven inbound provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-concepts).

## Comparison: Inbound provisioning /bulkUpload API and Microsoft Graph Users API

We recommend noting the differences between the provisioning **/bulkUpload** API and the Microsoft Graph Users API endpoint: Payload format, operation result, and IT administrators retain control.

In an FAQ, learn how [the new inbound provisioning API differs from Graph Users API](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/inbound-provisioning-api-faqs).

## Deploy API-driven inbound provisioning

1. [Create an API-driven provisioning app](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-configure-app).
2. For **Active Directory**, [configure API-driven inbound provisioning app](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-configure-app). For **Microsoft Entra ID**, [configure API-driven inbound provisioning app](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-configure-app).
3. [Grant access to inbound provisioning API](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-grant-access)
4. [Customize user provisioning attribute mappings](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/customize-application-attributes)
5. [Sync custom attributes](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-custom-attributes)

To learn more, see the following Quickstart guides about API-driven inbound provisioning with:

- [cURL](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-curl-tutorial)
- [Postman](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-postman)
- [Graph Explorer](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-graph-explorer)
- [PowerShell](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-powershell)
- [Azure Logic Apps](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/inbound-provisioning-api-logic-apps)

### Outbound app provisioning

You can provision to Software-as-a-Service \(SaaS\) apps, using a System for Cross-Domain Identity Management \(SCIM\).

Discover more about [SCIM synchronization with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/architecture/sync-scim).

### Configure provisioning with a SCIM endpoint

SCIM 2.0 is a standardized definition of two endpoints **/Users** and **/Groups**.

See more details in the tutorial, [develop, and plan provisioning for a SCIM endpoint in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/use-scim-to-provision-users-and-groups).

## Deploy SaaS sample-app provisioning

The [Microsoft Entra ID application gallery](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list) displays available apps for user provisioning. Select up to four apps for your environment, or choose from these popular apps to enable automatic user provisioning:

- [ServiceNow](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/servicenow-provisioning-tutorial)
- [Salesforce](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/salesforce-provisioning-tutorial)
- [Box](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/box-userprovisioning-tutorial)
- [Cisco Webex](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/cisco-webex-provisioning-tutorial)
- [Workplace by Facebook](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/workplace-by-facebook-provisioning-tutorial)
- [Zoom](https://learn.microsoft.com/en-us/azure/active-directory/saas-apps/zoom-provisioning-tutorial)

### \(Optional\) Provision to on-premises apps

Users and schema defined in the cloud support provisioning from custom schema extensions to app-specific properties.

To learn more, go to [app provisioning samples for SCIM-enabled apps](https://learn.microsoft.com/en-us/azure/active-directory/app-provisioning/on-premises-scim-provisioning).

## Lifecycle workflows

Lifecycle workflows are an identity governance feature to manage Microsoft Entra users by automating Joiner, Mover, and Leaver events for employees. Use the feature to schedule tasks for before, during, or after an event. Workflows can run on demand. With built-in tasks, you can generate temporary credentials, send emails, update user attributes, and memberships, and remove licenses.

Learn more in the [overview of lifecycle workflow APIs](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflows-overview?view=graph-rest-1.0&preserve-view=true).

### Joiner

A Joiner is an individual who needs access. When you onboard new employees, use templates and workflows to make processes more efficient and faster.

### Mover

A Mover is an individual moving between boundaries in an organization, for instance, the employee goes from a role in Sales to one in Marketing. The movement might require more, or different, access, and authorization.

### Leaver

The Leaver no longer needs access, such as terminated or retiring employees. Effective Leaver workflows reduce the risk of unauthorized data access, after termination. Therefore, handle Leaver personal information in compliance with regulations and policies. Use customizable workflow templates for timely, reliable, and graceful resource-access removal.

**Remove application access**

Microsoft Entra ID provisioning service keeps source and target systems in sync. Deprovision an account when user access must end.

1. Unassign the user from one or more applications.
2. Delete the account from Microsoft Entra ID.
3. Set the **AccountEnabled** property to **False**.

   Note

   If an application supports the process, you can soft-delete users by default.

### Lifecycle workflows custom extensions

Use custom extensions to create workflows using tools like Azure Logic Apps. For workflows, you can enable custom task extensions to call out to external systems. For example, a Joiner workflow with a custom task extension assigns a Microsoft Teams number. Or, when a user becomes a Leaver, a separate workflow grants access to an email account for their manager. You can learn to [trigger Logic Apps based on custom task extensions](https://learn.microsoft.com/en-us/entra/id-governance/trigger-custom-task).

Note

To create a logic app resource for hosting, select **Consumption**. A consumption logic app has one workflow that runs in multitenant Azure Logic Apps.

To learn more, see the [App Service Environment overview](https://learn.microsoft.com/en-us/azure/app-service/environment/overview) and [Azure Logic Apps documentation](https://learn.microsoft.com/en-us/azure/logic-apps/logic-apps-overview).

## Deploy lifecycle workflows

1. [Synchronize attributes](https://learn.microsoft.com/en-us/azure/active-directory/governance/how-to-lifecycle-workflow-sync-attributes)
2. [Prepare user accounts](https://learn.microsoft.com/en-us/azure/active-directory/governance/tutorial-prepare-user-accounts)
3. [Automate prehire tasks for employees](https://learn.microsoft.com/en-us/azure/active-directory/governance/tutorial-onboard-custom-workflow-portal)
4. [Automate onboarding new employees](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-templates)
5. [Automate post-onboarding](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-templates)
6. [Real-time employee change](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-templates)
7. [Real-time employee termination](https://learn.microsoft.com/en-us/azure/active-directory/governance/tutorial-offboard-custom-workflow-portal)
8. [Employee group membership changes](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-templates)
9. [Employee job profile change](https://learn.microsoft.com/en-us/entra/id-governance/lifecycle-workflow-templates)
10. [Automate preoffboarding](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-templates)
11. [Automate offboarding](https://learn.microsoft.com/en-us/azure/active-directory/governance/tutorial-scheduled-leaver-portal)
12. [Automate post-affboarding](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-templates)
13. [Trigger Logic Apps with custom extensions](https://learn.microsoft.com/en-us/azure/active-directory/governance/trigger-custom-task)

### Supported tasks and workflows

The table lists tasks and workflow according to Joiner, Mover, Leaver status.

| Category | Tasks and workflows |
| --- | --- |
| Joiner | [Send welcome email to new-hire](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Joiner | [Send onboarding reminder email](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Joiner | [Generate temporary access pass \(TAP\) and send it by email to the new-hire's manager](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Mover | [Send notification email to manager about a user move](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Joiner, Mover | [Request user access package assignment](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Joiner, Mover, Leaver | [Add user to groups](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Joiner, Mover, Leaver | [Add user to teams](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Joiner, Leaver | [Enable user account](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Joiner, Mover, Leaver | [Run a custom task extension](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Disable user account](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Joiner, Mover, Leaver | [Remove user from groups](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Remove user from all groups](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Remove user from teams](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Remove user from all teams](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver, Mover | [Remove user access package assignments](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Remove all user access package assignments](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Cancel all pending user access package assignment requests](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Remove all user license assignments](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Delete user](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Send email to user's manager before before last day](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Send email to user's manager on last day](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |
| Leaver | [Send email to user's manager after last day](https://learn.microsoft.com/en-us/azure/active-directory/governance/lifecycle-workflow-tasks) |

## Next steps

- [Introduction to Microsoft Entra ID Governance deployment guide](https://learn.microsoft.com/en-us/entra/architecture/governance-deployment-intro)
- Scenario 1: Employee lifecycle automation
- [Scenario 2: Assign employee access to resources](https://learn.microsoft.com/en-us/entra/architecture/governance-deployment-employee-access)
- [Scenario 3: Govern guest and partner access](https://learn.microsoft.com/en-us/entra/architecture/governance-deployment-guest-access)
- [Scenario 4: Govern privileged identities and their access](https://learn.microsoft.com/en-us/entra/architecture/governance-deployment-privileged-identities)
