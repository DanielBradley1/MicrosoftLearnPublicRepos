<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/get-ready-copilot-sharepoint-advanced-management -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# Get ready for Microsoft Copilot and agents with SharePoint Advanced Management

Microsoft Copilot and agents work best for your organization when your content is up to date and well governed. Copilot and agents retrieve data from Microsoft Graph and respect existing permissions, sharing settings, and policies.

This article describes how to prepare your environment for Copilot and agent usage by using capabilities in [SharePoint Advanced Management](https://learn.microsoft.com/en-us/sharepoint/advanced-management).

## Step 1: Use Content Management Assessment

The [Content Management Assessment hub](https://learn.microsoft.com/en-us/sharepoint/content-management-assessment) provides administrators with actionable insights and recommendations. It runs a suite of essential reports that surface key findings and categorize sites that might require attention.

[![Screenshot of the Content Management Assessment hub in SharePoint.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/start-content-management-assessment.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/start-content-management-assessment.png#lightbox)

The Content Management Assessment provides a simple, guided process for administrators to:

- Identify potentially overshared content
- Find issues or risks \(such as inactive or ownerless sites\)
- Define Copilot readiness for the organization
- Ensure compliance and maintain data integrity
- Receive actionable recommendations for remediation
- Track progress over time with recurring assessments

This hub helps make content governance accessible and actionable, even for administrators who might not have deep technical expertise yet.

### Access the Content Management Assessment hub

1. In the SharePoint admin center, in the navigation pane, select **Advanced Management**.
2. Select **Start assessment**.

After the assessment runs, review the findings, and take appropriate actions. Rerun the assessment every 30 days to track your progress and address any new issues.

## Step 2: Employ site lifecycle management and archiving

Site lifecycle management policies and archiving help ensure that your sites are up to date, compliant, and use storage efficiently. These capabilities help ensure Copilot and agentic experiences reference current content and can reduce storage costs.

### Site lifecycle management

[Site lifecycle management policies](https://learn.microsoft.com/en-us/sharepoint/site-lifecycle-management) help reduce content sprawl by automating the process of ensuring that your organization's SharePoint sites are well governed.

[![Screenshot of the Site lifecycle management page in the SharePoint admin center.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/site-lifecycle-management.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/site-lifecycle-management.png#lightbox)

When you set up your site lifecycle management policies, the system automatically identifies potential problems. You can configure enforcement actions and email notifications that ask site owners or administrators to take action.

#### View or create site lifecycle management policies

1. In the SharePoint admin center, in the navigation pane, select **Site lifecycle management**.
2. Under a category, such as **Inactive site policies**, **Site ownership policies**, or **Site attestation policies**, select **Open**.

#### Site lifecycle management policies

Site lifecycle management policies include the following:

- [Site ownership policies](https://learn.microsoft.com/en-us/sharepoint/site-ownership-policy) that support effective site management and reduce the risk of ownerless sites. You can set minimum owner or administrator counts and automate notifications when sites don't meet the criteria.
- [Inactive site policies](https://learn.microsoft.com/en-us/sharepoint/inactive-site-policy) that automatically detect inactive sites and notify site owners by email.
- [Site attestation policies](https://learn.microsoft.com/en-us/sharepoint/request-site-attestations) that ask site owners or site administrators to check and confirm the accuracy of site information, including site necessity, owners, members, permissions, and sharing settings.

### Microsoft 365 Archive

Use [Microsoft 365 Archive](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-overview) to retain inactive content, such as ownerless or inactive sites. This approach helps reduce your storage consumption and improves Copilot optimization. When you archive a site:

- The site moves to a Microsoft 365 Archive storage tier.
- The site no longer consumes active SharePoint storage quota.
- Content, permissions, and metadata are preserved.
- Users can't access the site until it's reactivated.
- Copilot isn't trained on archived content.

You can manage archived sites on the **Archived sites** page.

#### Set up and use Microsoft 365 Archive

See the following resources:

- [Set up Microsoft 365 Archive](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-setup)
- [Manage Microsoft 365 Archive](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-manage)
- [End-user experience in Microsoft 365 Archive](https://learn.microsoft.com/en-us/microsoft-365/archive/archive-end-user)

## Step 3: Prevent accidental oversharing

To help prevent accidental oversharing in Copilot and agentic experiences, adjust sharing settings for SharePoint and OneDrive. Use data access governance reports and insights to identify and prioritize oversharing risks. Restrict access to sensitive content.

### Adjust sharing settings for SharePoint and OneDrive

By default, SharePoint sets sharing settings to the most permissive option. You can set sharing settings for SharePoint, OneDrive, and links to files or folders.

[![Screenshot of sharing settings in the SharePoint admin center.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/sharing-settings.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/sharing-settings.png#lightbox)

You can also specify expiration and permission options for links.

#### Adjust sharing settings

1. In the SharePoint admin center, in the navigation pane, expand **Policies**, and then select **Sharing**.
2. Starting at the top, specify your settings, and then select **Save**.

   To get help with this task, see [Manage sharing settings for SharePoint and OneDrive](https://learn.microsoft.com/en-us/sharepoint/turn-external-sharing-on-or-off).

### Use data access governance reports to identify oversharing risks

[Data access governance reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports) help you identify sites that contain potentially overshared or sensitive content.

[![Screenshot of the data access governance page in the SharePoint admin center.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/data-access-governance.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/data-access-governance.png#lightbox)

Several reports are available, including [snapshot reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports#what-are-snapshot-reports) and [activity reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports#what-are-activity-reports).

#### Access data access governance reports

1. In the SharePoint admin center, expand **Reports**, and then select **Data access governance**.
2. Under a category, select **View reports**.

#### Start with these reports

- The [site permissions baseline report](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-site-permissions-report) helps you understand your organization's overall access exposure. This report provides you with a snapshot that shows your current permission structure across SharePoint and OneDrive sites, and enables you to identify sites that need immediate attention.
- The [site permissions for users report](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-site-permissions-users-report) lists all the sites a given user can access so you can determine whether permissions need to be adjusted.
- Activity-based reports:

  - The [Everyone except external users \(EEEU\) report](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-everyone-except-external-user-report) helps you identify the top 100 sites where content was shared with your entire organization in the past 28 days, and security policies applied to those sites.
  - The [sharing links activity reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-sharing-links-report) help you identify sites where users created the most sharing links within the last 28 days. You can see a list of sites with the highest number of "Anyone" links, "People in the organization" links, and "Specific people" links.

### Use AI insights to interpret report findings

The [AI insights](https://learn.microsoft.com/en-us/sharepoint/ai-insights) feature reduces the manual effort required to review reports and helps mitigate content governance problems. It uses a language model to identify patterns and potential problems from reporting and provides actionable recommendations to solve problems.

[![Screenshot of site lifecycle management insights dashboard in SharePoint admin center.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/ai-insights-inactive-sites.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/ai-insights-inactive-sites.png#lightbox)

Where available, use AI-generated insights to help interpret report findings and identify recommended actions.

The AI insights feature is available for these reports:

- [Sharing links activity reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-sharing-links-report)
- [Sensitivity label snapshot report](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-sensitivity-label-report)
- [Inactive site policy](https://learn.microsoft.com/en-us/sharepoint/inactive-site-policy), which helps identify inactive sites. After the policy runs, you can download a report in CSV format.
- [Change history reports](https://learn.microsoft.com/en-us/sharepoint/change-history-report) which show site actions or organization setting changes made within the last 180 days

#### Generate AI insights

1. In the SharePoint admin center, in the navigation pane, expand **Reports**, and select an option, such as **Data access governance** or **Change history**.
2. Select a report, look for the **Get AI insights** button, and then select it to generate AI insights.

### Restrict access to sensitive content

If necessary, restrict site access by using [Restricted Access Control](https://learn.microsoft.com/en-us/sharepoint/restricted-access-control) to help prevent oversharing. By using Restricted Access Control, you grant access to SharePoint sites by using groups, such as Microsoft Entra security groups or Microsoft 365 groups. Users who aren't part of the specified group can't access the site or its contents, even if they had prior access through permissions or a link.

[![Screenshot of site-level access restriction settings in SharePoint.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/enable-site-level-access-restriction.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/enable-site-level-access-restriction.png#lightbox)

Use your Restricted Access Control policy to:

- Limit site access to a defined group of users
- Prevent broad or unintended access
- Ensure that only authorized users can access content and see it in Copilot

#### Restrict site access

1. Set up or identify a security group in Microsoft Entra or a Microsoft 365 group \(see [Microsoft Entra: Group types](https://learn.microsoft.com/en-us/entra/fundamentals/concept-learn-about-groups#group-types)\).
2. In the SharePoint admin center, in the navigation pane, expand **Policies**, and then select **Access control**.
3. Select the **Enable site access restriction** option.

   To enable site administrators to control who can access their sites, select **Delegate site access restriction control to site administrators**.
4. Select **Save**.

For more information, see [Restrict access to a SharePoint site](https://learn.microsoft.com/en-us/sharepoint/restricted-access-control).

### Control content discovery of high-risk sites

If you have high-risk sites that you want to prevent accidental discovery in Copilot or agentic experiences, use [Restricted Content Discovery](https://learn.microsoft.com/en-us/sharepoint/restricted-content-discovery) for those sites.

[![Screenshot of Restricted Content Discovery settings for a site in the SharePoint admin center.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/enable-restrict-content-discovery.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/enable-restrict-content-discovery.png#lightbox)

Restricted Content Discovery helps to:

- Prevent content from appearing in Copilot or agentic experiences and in organization-wide search queries
- Reduce accidental exposure while leaving site permissions unchanged

Restricted Content Discovery is useful for content that must remain accessible, but shouldn't be broadly discoverable.

#### Identify high-risk sites

1. Use your tools and reports, such as the SharePoint Admin Agent and data access governance reports, to see these risk signals:

   - Broad sharing through "Anyone," "Everyone," and organization-wide links
   - Large audiences with excessive permissions
   - Broken permission inheritance and complex access models
   - Sensitive content with weak protection
   - Unlabeled or public sites
   - Governance gaps with ownerless, inactive, or unreviewed sites


   Sites where multiple risk signals overlap are considered high risk. Examples include:


   - Sites that contain sensitive data and that have "Anyone" sharing links
   - Public sites with no owner
   - Large audiences with broken permission inheritance

2. Use SharePoint Advanced Management tools and reports to highlight sites with oversharing or exposure risk.

   - [Data access governance reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports), such as [site permissions reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports) and [sharing link activity reports](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-sharing-links-report)
   - [AI insights](https://learn.microsoft.com/en-us/sharepoint/ai-insights)
   - [SharePoint Admin Agent](https://learn.microsoft.com/en-us/sharepoint/content-governance-agent)

3. Create a list of high-risk sites that you want to restrict from content discovery.

#### Restrict content discovery

1. In the SharePoint admin center, expand **Sites**, and then select **Active sites**.
2. Select a site to open its flyout. On the flyout, select the **Settings** tab.
3. Under **Restrict content discovery**, select **On**. Then select **Save**.

For more information, see [Restrict discovery of SharePoint sites and content](https://learn.microsoft.com/en-us/sharepoint/restricted-content-discovery).

## Step 4: Use the SharePoint Admin Agent

The [SharePoint Admin Agent](https://learn.microsoft.com/en-us/sharepoint/content-governance-agent) responds to your questions by gathering the relevant data and reports, offering analysis and recommendations, and suggesting other prompts. Ask a question, such as "Show me how my content is distributed across my tenant," and get useful information with suggested prompts and next steps.

[![Screenshot showing the SharePoint Admin Agent open in the Copilot app](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/admin-agent-open-in-copilot.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/admin-agent-open-in-copilot.png#lightbox)

### Open the SharePoint Admin Agent

Take one of the following steps:

- In the Microsoft Copilot app, expand **Agents**, and search for *SharePoint Admin Agent*.
- In the SharePoint admin center, select the **Copilot** button, and then select the **View prompts** button in the lower corner of the Copilot pane.
- In Microsoft Teams, select **Apps**, and then search for *SharePoint Admin Agent*.

For more information, see [SharePoint Admin Agent](https://learn.microsoft.com/en-us/sharepoint/content-governance-agent).

## Step 5: Implement backup and restore procedures

Business continuity requires a backup and restore solution, such as [Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/backup). In the event of an accidental or malicious data deletion or overwriting, it's important for your data to be protected and easily recoverable.

[![Screenshot of the Microsoft 365 Backup page in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/microsoft-365-backup.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/get-ready-copilot-sharepoint-advanced-management/microsoft-365-backup.png#lightbox)

With Microsoft 365 Backup:

- Data never leaves the Microsoft 365 data trust boundary and honors the geographic locations of your current data residency.
- Backups are immutable unless the backup tool administrator expressly deletes them.
- OneDrive, SharePoint, and Exchange have multiple physically redundant copies of your data to mitigate the impact of physical disasters.

### Get started with Microsoft 365 Backup

1. In the Microsoft 365 admin center, in the navigation pane, expand **Settings**, and then select **Microsoft 365 Backup**.
2. Review the information on the page to learn more and get started.

**To learn more about Microsoft 365 Backup**, see the following resources:

- [Overview of Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-overview)
- [Set up Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-setup)
- [Create, view, and edit backup policies in Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-view-edit-policies)
- [Restore data in Microsoft 365 Backup](https://learn.microsoft.com/en-us/microsoft-365/backup/backup-restore-data)
