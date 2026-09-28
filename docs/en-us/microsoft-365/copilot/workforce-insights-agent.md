<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/workforce-insights-agent -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Workforce Insights agent

Important

The Workforce Insights agent is in the Microsoft Frontier program and subject to change. For more information, see [Get started with the Microsoft Frontier program](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/get-started-frontier).

The Workforce Insights agent helps organizational leaders and their specified delegates:

- Understand organization composition and landscape of users of key attributes within their organizations.
- Perform and summarize guidance and best practices for workforce planning based on skills.
- Identify skills and suggest improvements to organizational structure.
- Find team members in your organization and filter by attributes such as level, location, title, etc.

The Workforce Insights agent uses information from:

- [Organizational Data](https://learn.microsoft.com/en-us/viva/organizational-data)

  - Organizational data describes the users in your organization.

- [Custom attributes](#data-available-in-the-workforce-insights-agent) sent to Workforce Insights
- [People Skills data](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-overview)

Important

You can only search for information that's available to you about your team. Responses are based on your role, and policies set by your admin and organization.

## Licensing and tenant requirements

Workforce Insights is only available to users with paid Microsoft Copilot licenses. In addition:

- Delegates also require a paid Microsoft Copilot license.
- People Skills data also require appropriate licensing.

Once you have the appropriate licenses, you can start using the Workforce Insights agent.

## Responsible AI, data privacy, and security

For information on responsible AI principles and usage, see the following articles:

- [Responsible AI Principles and Approach](https://www.microsoft.com/ai/principles-and-approach?msockid=3be31cda99b962db1b5a0a8398f063ed)
- [Responsible AI: Ethical policies and practices](https://www.microsoft.com/ai/responsible-ai)
- [Data privacy and security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
- [People Skills data and AI guidelines](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-data-and-ai-guidelines)

## Customize how managers are identified

By default, the Workforce Insights agent identifies managers based on organizational hierarchy: any employee with one or more direct reports is considered as a manager. Some organizations, however, use a different definition based on internal HR policies.

To support these scenarios, you can override the default logic by providing a `SupervisorIndicator` column in your organizational data. This column becomes the authoritative signal for determining manager status in manager-related questions, insights, and analytics. This column ensures that manager counts, manager-to-individual contributor \(IC\) ratios, and related metrics align with your organization's formal definition of a manager.

Important

The `SupervisorIndicator` configuration is fully data-driven. Adding the `SupervisorIndicator` column doesn't change your reporting hierarchy, manager-employee relationships, access control, delegation, or privacy enforcement. Features such as delegation and manager-confidential access continue to rely on direct reporting relationships.

### When to use the `SupervisorIndicator`

Use this feature if your organization:

- Excludes certain roles from being considered as managers such as contractor sponsors
- Distinguishes people managers from other supervisory roles
- Uses a formal manager definition that differs from reporting hierarchy

If your definition of a manager already aligns with having direct reports, no additional configuration is required.

### How Workforce Insights interprets `SupervisorIndicator`

Workforce Insights interprets `SupervisorIndicator` using the following parameters:

- Employees defined as "Managers" are treated as managers in Workforce Insights.
- Employees defined as "Individual contributors" are treated as ICs, even with direct reports.
- If the column isn't provided, Workforce Insights uses the default logic based on direct reports.

Note

This override applies only to manager status used in chat responses and analytics.

For instructions on how to upload the SupervisorIndicator attribute, see [Upload and maintain organizational data in the Microsoft admin center](https://learn.microsoft.com/en-us/viva/insights/advanced/admin/upload-org-data-admin-center#how-to-prepare-upload-and-manage-your-data-in-the-microsoft-365-admin-center).

The column must contain one of the following values. Values are case-insensitive but must otherwise match exactly.

- Boolean: `True`, `False`
- Enumerated strings:

  - Manager: `Mgr`, `Mgr+`
  - Individual contributor: `ic`

If unsupported values are used, such as additional labels, different spelling, or unexpected formats, Workforce Insights can't reliably determine manager status.

## Configure a custom AI disclaimer

You can configure a tenant‑wide disclaimer footer for the Workforce Insights Agent. The disclaimer appears under the chatbox and in the footer of the homepage for all eligible users. You can use the disclaimer to provide organizational context, data‑usage guidance, links to authoritative dashboards, or other notices that help users interpret Workforce Insights responses.

The footer supports basic text formatting \(bold and italic\) and hyperlinks. You can highlight key information and link to resources such as internal Power BI dashboards or data governance documentation, while maintaining a consistent user experience.

**To add and manage the disclaimer footer:**

1. Go to the Workforce Insights landing page.
2. Select **Custom AI disclaimer** to add and manage the disclaimer.

## Organization-specific prompts

Note

Organization-specific prompts are optional. You don't have to create organizational-specific prompts to use the Workforce Insights agent.

Administrators can add custom organization-specific prompts to the Workforce Insights agent home page. These prompts guide leaders and delegates to the questions, workflows, and standards that matter most to your organization while preserving the core Workforce Insights experience.

Organization-specific prompts appear alongside Microsoft-provided suggested prompts and are visible tenant-wide.

Note

Prompt responses are subject to existing data access and delegation policies.

### Data access, privacy, and permissions

Organization specific prompts don't override data access policies. Responses are generated only from data the user is already permitted to access.

- Manager confidential or restricted attributes remain gated by existing access policies.
- If a prompt references data the user doesn't have access to, the response might be limited or unavailable.

For example, a prompt that relies on manager-confidential attribute return results only for users with appropriate manager or delegate access.

### What are organization-specific prompts?

Organization-specific prompts are admin-created prompt cards displayed under **From your organization on the Workforce Insights** home page. The prompts:

- Reinforce commonly asked, organization-relevant questions
- Provide consistent phrasing for workforce analysis
- Help users get started faster with trusted prompts

Note

Organization-specific prompts supplement Microsoft-provided suggested prompts. Microsoft-provided suggested prompts can't be removed or replaced.

### How organization-specific prompts work

Administrators can create up to six organization-specific prompts per tenant. Each prompt includes:

- Prompt title: A short label shown on the prompt card
- Display prompt: A concise, user facing question shown on the home page
- Extended prompt \(optional\): Additional instructions or context used by Copilot when generating a response

The display prompt stays short and scannable on the home page. Use the extended prompt to add guidance without cluttering the user interface.

Important

When a user selects a prompt card, only the extended prompt, if provided, is inserted in the message box. The display prompt isn't included automatically. To include the display prompt, you must repeat the display prompt in the extended prompt.

Prompts are saved at the tenant level, so all eligible users see the same prompts.

### Who can create and manage prompts?

Important

Before you add custom prompts, test the prompts to ensure that each prompt works, and the Workforce Insights agent returns the expected results.

Only authorized [Organizational Data Source Administrators](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#organizational-data-source-administrator) can create, edit, reorder, or delete organization-specific prompts. Prompt management is available from the Workforce Insights admin settings experience. End users can't modify prompts.

**To create and manage prompts:**

1. Go to the Workforce Insights landing page.
2. Select **Organization-specific prompts** to add and manage prompts.

### Where users see organization specific prompts

On the Workforce Insights agent home page, prompts are grouped into:

- Microsoft-provided suggested prompts, which might vary based on role and delegation
- Organization-specific prompts created by your admin

Organization specific prompts are visually distinct, so users know they were added by their organization. If fewer than six organization specific prompts are configured, the remaining space is filled by suggested prompts.

#### Example

- Prompt title: team location coverage
- Display prompt: Show me the distribution of my team by location and time zone
- Optional extended prompt: Show me the distribution of my team by location and time zone. Include a breakdown by primary work location and time zone. Highlight any locations with limited overlap in core working hours and call out potential collaboration risks

### Limitations and considerations

- You can add up to six organization specific prompts per tenant
- Default Microsoft-provided prompts can't be edited or removed
- Prompts are additive, and don't replace suggested prompts
- Prompts apply tenant-wide and aren't targeted to specific groups or roles in the current experience

These limits help ensure a consistent, predictable experience for all users.

### Best practices for writing effective organization-specific prompts

To get the most value from organization-specific prompts:

- Keep display prompts short and action oriented
- Use extended prompts to clarify intent, assumptions, or preferred framing
- Avoid references to data or attributes not available in your organizational data
- Align prompts to real questions leaders and delegates already ask

Clear, well-written prompts improve consistency, reduce ambiguity, and build trust in the results.

## Start using the Workforce Insights agent

**To start using the Workforce Insights agent:**

1. Upload organizational data. For more information on best practices when using organizational data, see [Organizational Data in Microsoft 365](https://learn.microsoft.com/en-us/viva/organizational-data).
2. Understand data access policies and delegation.

   1. [Use admin controls to manage access to Workforce Insights](#use-admin-controls-to-manage-access-to-the-workforce-insights-agent-in-your-organization)
   2. Manage delegation policies

3. Download the Workforce Insights agent from the Agent Store in Microsoft Copilot.
4. Set up [People Skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-setup).

## Use admin controls to manage access to the Workforce Insights agent in your organization

You have several controls to deploy the Workforce Insights agent in your organization. You should review the controls to manage Workforce Insights agent deployment and access in your tenant.

The following controls are available:

| Control | Description |
| --- | --- |
| Pilot by restricting access to some users | Restrict access to the agent to only specified users or groups. You can choose which users the agent is deployed to, and to whom it's available to install. Use this control for piloting. |
| Deploy the agent \(recommended\) | Install the agent on behalf of users in your organization. This action makes the agent active and usable for specific users or groups without them having to install it themselves. |
| Remove/block the agent | You can completely block access to the Workforce Insights agent for all users or remove a previously deployed agent from your inventory. |

For more information on how to manage agents, see [Manage agents for Microsoft Copilot in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps?toc=%2Fcopilot%2Fmicrosoft-365%2Ftoc.json&bc=%2Fcopilot%2Fmicrosoft-365%2Fagent-framework%2Fbread%2Ftoc.json).

## Manage delegation policies

As a manager or leader using the Workforce Insights agent, you can assign a delegate, or multiple delegates, to access the organizational data that's available to you about your team.

For example, if you're a manager, you might have access to confidential attributes about your team. This custom attribute could be called `salary`. If you assign a delegate to access this attribute, the delegate can query data within this column. When you use delegates, it helps managers and leaders conduct analysis with the support of their team.

### Delegation admin controls

| Control | Description |
| --- | --- |
| Disable the ability for a user to assign delegates | As the admin, you can restrict users from assigning a delegate to view organizational insights. Use the Microsoft 365 control access to features with PowerShell under the module name WorkforceInsights. |
| Assign delegates or revoke delegates on behalf of a user | Starting in January 2026, as the admin, you can use PowerShell commandlets to assign or revoke delegates access on behalf of a user. |

### Assign delegates

**To assign delegates:**

1. Go to the Workforce Insights landing page.
2. On the Workforce Insights landing page, navigate to the Manage data access dropdown. In this page, you can:

   1. View all your delegates.
   2. Request delegation from another manager or leader in your organization.

3. Once you assign access, the delegate receives a notification in Teams to use the Workforce Insights agent.

## Request data access

Delegates can request access through a similar workflow.

Note

If the user is without a team, that user can't delegate.

**To request access:**

1. Go to the Workforce Insights landing page.
2. On the Workforce Insights landing page, navigate to the Request data access dropdown.
3. Enter the following information:

   1. The person you're requesting access from.
   2. Optional. You can add a message to provide context or reasons behind the request for access.

4. When the request is received, the manager or leader grants or denies access.

## Data available in the Workforce Insights Agent

The following explains:

- How the Workforce Insights agent uses different types of data that is supported when made available in your organization
- How you can configure data for the Workforce Insights agent to use

| Data type | Description |
| --- | --- |
| Public attributes | Public attributes include general information seen by all users in the tenant, such as work email, name, job title, and department.<br><br>The attributes uploaded by the tenant are available to the Microsoft 365 profile. The tenant's users and Microsoft 365 apps have access to the attributes. The data used for public attributes used by Workforce Insights depends on the precedence of the data used in Microsoft 365 User Profile. For more information, see [Understand how organizational data is used and retained in Microsoft 365](https://learn.microsoft.com/en-us/viva/orgdata-data-usage#data-usage).<br><br>You can find the complete list of public attributes available to Workforce Insights in the [Organizational Data in Microsoft 365 - Attribute reference](https://learn.microsoft.com/en-us/viva/orgdata-attributes). |
| People skills | The Workforce Insights Agent can use the People Skills data that's available in your organization. Before you can use People Skills data, you must [set up People Skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-setup) in your tenant first. |
| Custom attributes | Custom attributes are attributes that you might want to add to the public attributes to enhance the usefulness of the Workforce Insights agent. These attributes need to be explicitly uploaded and made available to the Workforce Insights service.<br><br>Use the information in [Map attributes and set access for Microsoft 365, Copilot, and Viva apps](https://learn.microsoft.com/en-us/viva/map-attributes-set-access#4-choose-attribute-access-for-apps) to make data available to the Workforce Insights service.<br><br>In addition to making custom attributes available for the service, you must:<br><br>1. Configure the use of the custom attributes by [assigning access policies](https://learn.microsoft.com/en-us/viva/set-access-policies).<br>2. Add the attribute metadata for the agent to use. You can use the [Custom column best practices](#custom-column-best-practices) section to help you attribute the metadata.<br><br>Other helpful resources:<br><br>- To upload public and custom attributes, see [Import your organizational data with a `.csv` file](https://learn.microsoft.com/en-us/viva/import-orgdata)<br>- [Manage delegation access policies](#manage-delegation-policies) |

## Custom column best practices

When creating custom columns, it's important to ensure that names and descriptions are clear, consistent, and meaningful. The following table explains a specific input you must provide, such as the column name, description, data type, and data quality. The table offers guidance on how to define custom columns effectively.

After reviewing these guidelines, see the [custom column examples](#custom-column-examples) that bring all these elements together to illustrate what an ideal column configuration looks like in practice.

| Input | Guidance |
| --- | --- |
| Column Name | Choose a column name that's concise and descriptive of its purpose. Avoid abbreviations or ambiguous terms that could lead to confusion. Think of column names like labels on a form or headings in a spreadsheet. The column name should clearly tell someone what information belongs in that column without needing extra explanation. Don't include detailed usage instructions or data definitions in the name. Usage instructions and data definitions belong in the description. |
| Data Type | Select the correct data type for the column. The options are:<br><br>- String<br>- Boolean<br>- DateTime<br>- Double<br>- Integer<br><br>Using an incorrect type can lead to poor performance and inaccurate results.<br><br>Clean and normalize data before uploading by ensuring consistent spelling and capitalization. Avoid inconsistent values such as:<br><br>- `Software Eng` versus `Software Engineer`<br>- `Washington` versus `WASHINGTON`<br>- Use full terms instead of acronyms. `Product Manager` instead of `PM`<br><br>The number of unique values per column is limited to `100` for string data types. There's no hard limit on the number of values, but performance is better if the number of unique values is constrained. These limits don't apply to numbers or dates. |
| Semantic Overlap | Avoid creating multiple columns that represent similar concepts. Significant overlap between columns can lead to inconsistent or unpredictable results. If two columns serve nearly the same purpose, consider consolidating them. |
| Column Description | After the **Organizational Data Admin** completes the **MODIS \(Microsoft Organizational Data Ingestion System\) process** where they ingest [organizational data](https://learn.microsoft.com/en-us/viva/organizational-data) and select which columns to send to Workforce Insights agent, there might be a short latency period before the data becomes available for configuration. **In most cases, this takes a few hours, though in some scenarios it might take longer**.<br><br>Column descriptions give the Workforce Insights agent the context to use the data correctly. The descriptions are AI-generated, but administrators must review and confirm that the descriptions reflect their organization's data and definitions.<br><br>In the [configuration page](https://aka.ms/WorkforceInsightsAdminHome), there are two types of status messages informing you about:<br><br>1. The number of columns that need attention<br>2. The number of columns that were changed<br><br>Custom columns without a confirmed description aren't used by the Workforce Insights agent. Column descriptions changes take effect immediately after you save the changes.<br><br>**What to include in a column description**<br><br>A good column description clearly explains:<br><br>- What the column represents<br>- How the data is intended to be used<br>- Important constraints or nuances, such as:<br><br>  - When the meaning isn't obvious from the values<br>  - When the column is derived from multiple data elements<br>  - When values are limited to a defined set or format<br><br>AI-generated descriptions often already include much of this information, but administrators should verify accuracy and add organization-specific context as needed.<br><br>**Important considerations:**<br><br>- A blank value isn't accepted in any column description. Use the AI-generated description or add/edit your description<br>- AI-generated descriptions aren't final until an administrator confirms them<br>- Confirmed descriptions are stored at the tenant level and apply to all eligible users<br>- Descriptions can be updated as data definitions change<br><br>To upload and maintain attributes, see [Upload and maintain organizational data in the Microsoft admin center](https://learn.microsoft.com/en-us/viva/insights/advanced/admin/upload-org-data-admin-center#how-to-prepare-upload-and-manage-your-data-in-the-microsoft-365-admin-center). |

## Custom column examples

### Example 1: `JobTitle`

| Input | Value |
| --- | --- |
| Column Name | `JobTitle` |
| Column Description | Represents the internal classification of an employee's job title. It contains the employee's level \(Junior or Senior\) and role \(Project Manager or Software Engineer\). Possible values are:<br><br>- Junior Project Manager<br>- Senior Project Manager<br>- Junior Software Engineer<br>- Senior Software Engineer |
| Data Type | String |
| Data | `["Junior Project Manager", "Senior Project Manager", "Junior Software Engineer", "Senior Software Engineer"]` |
| Explanation | The data in the column being built from the employee's level and role is specified in the description. In addition, since the number of candidate values is small, we can list all possible values in the description. While it isn't necessary, listing all possible values can help increase accuracy. The data is also clear on the roles, using `Project Manager` instead of the acronym `PM`. |

### Example 2: `ManagerSpanBand`

| Input | Value |
| --- | --- |
| Column Name | `ManagerSpanBand` |
| Column Description | Categorizes a manager's number of direct reports into defined bands used for workforce planning and load balancing. Direct reports calculated weekly from the latest employee to manager relationships and excludes vendor or contingent workers. Band definitions are:<br><br>- S \(Small\) for one to five directs<br>- M \(Medium\) for six to 10 directs<br>- L \(Large\) for 11 to 15 directs<br>- XL \(Very Large\) for 16 or more directs<br>- Managers with zero directs and managers with invalid relationship data show up as "Not Applicable" |
| Data Type | String |
| Data | `["S","M","L","XL","Not Applicable"]` |
| Explanation | The name alone doesn't reveal thresholds, refresh cadence, or exclusions. The description must define these rules and edge cases. Without explicit bands and exception handling, interpretations could vary across queries. |

### Example 3: `WorkAnniversaryDate`

| Input | Value |
| --- | --- |
| Column Name | `WorkAnniversaryDate` |
| Column Description | Indicates the official date used to determine an employee's continuous service tenure for organizational purposes such as milestone recognition, service awards, and vacation accrual eligibility. Values are in `DD/MM/YYYY` format.<br><br>This date should always be used to calculate work anniversaries rather than HireDate, as it reflects continuous service and accounts for breaks or adjustments in employment history. |
| Data Type | DateTIme |
| Explanation | The description must specify that this date is used for tenure-related calculations rather than HireDate, as this distinction isn't evident from the column name alone. Including the format \(`DD/MM/YYYY`\) helps ensure clarity. |

For additional data guidance, see [Import your organizational data with a .csv file](https://learn.microsoft.com/en-us/viva/import-orgdata).

## Workforce Insights agent experiences and prompt examples

### Experiences

In the Workforce Insights agent, the following experiences can appear:

- Landing page with dynamic prompts and chat history.
- Responses can include inline visualizations such as graphs.
- Dynamically generated reports based on prompts.
- Share a report with another employee in your company. **You can only share the report via the provided link is only available to users with Copilot licenses.**

### Prompt examples you can use with the Workforce Insights agent

- Summarize my organization's distribution, my direct reports, and propose recommendations
- What is the individual contributor \(IC\) to manager ratio in my team?
- Surface top skills across the org and summarize strengths
- What is my team's level mix? Provide counts and percentage per level and highlight how this compares to other teams in my organization.
- Which roles benefit most from adopting AI tools?
- How did exits and hires change team sizes for my direct reports?
- How can I get the most from this Workforce Insights agent?
- Who has a work anniversary this quarter?

## FAQ

### What languages does the Workforce Insights agent support?

Being in the Frontier program, the Workforce Insights agent is optimized for English. Features like the landing page and chat work in all Microsoft Copilot languages but experiences like delegation, reports, and admin experiences are limited to English.

### How can I provide feedback on the Workforce Insights agent?

You can provide feedback in line after every prompt using the thumbs up/thumbs down option. Providing feedback can help the Workforce Insights team diagnose issues and receive feedback on response quality. You can also provide feedback by going opening **Microsoft Copilot** > select the **horizontal \(...\) ellipsis** > select **Send feedback** > follow the prompts to submit feedback.
