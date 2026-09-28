<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/frontline/shifts-for-teams-landing-page?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-02-05 -->

# Shifts for your frontline organization

Shifts, the schedule management app in Microsoft Teams, keeps your frontline workforce connected and in sync. It's built mobile first for fast and effective schedule management and communications across your frontline teams. With Shifts and Teams, frontline managers and workers can seamlessly manage schedules, communicate, and collaborate.

<iframe src="https://learn-video.azurefd.net/vod/player?id=7fd5b52f-a6c4-465b-915c-e28553534967" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Depending on your business needs, your organization can use Shifts as a standalone app or connect it to your workforce management \(WFM\) system. You can also use other Microsoft services and products to extend the capabilities of Shifts.

## Considerations before you deploy Shifts

As previously mentioned, your organization can opt to use Shifts as a standalone app or connect it to your WFM system. Connect Shifts to your WFM system if you want to:

- Know about the changes made to data through Shifts.
- Enforce the business rules and logic your organization configured in your WFM system before changes to data made by your frontline are saved to Shifts.
- Keep data in Shifts and in your WFM system in sync.

Here are options for integrating Shifts with external WFM systems.

| Workforce management system | Solution | Things to consider |
| --- | --- | --- |
| Reflexis Workforce Management version 4.3.2, 4.4, or 4.5 | [Reflexis Shifts connector for Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/frontline/shifts-connectors?view=o365-worldwide#reflexis-shifts-connector-for-microsoft-teams)  <br>\(Hosted and managed by Zebra\) | Shifts doesn't support every configuration and capability of your WFM system. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/frontline/shifts-connectors?view=o365-worldwide#reflexis-shifts-connector-for-microsoft-teams). |
| Any WFM system | [Create a custom integration to sync your workforce management system with Shifts](https://learn.microsoft.com/en-us/microsoft-365/frontline/shifts-custom-wfm-integration?view=o365-worldwide) | This option gives you the flexbility to integrate Shifts with any WFM system. You can set up your integration for a one-way or two-way data sync. |

## Deployment overview

Here's a quick overview for deploying Shifts in your organization.

1. **Create teams for your frontline locations**. You can choose to create your teams using the [deploy frontline dynamic teams at scale](https://learn.microsoft.com/en-us/microsoft-365/frontline/deploy-dynamic-teams-at-scale?view=o365-worldwide) experience in the Teams admin center.

   To learn more, see [How to find the best frontline team solution for your organization](https://learn.microsoft.com/en-us/microsoft-365/frontline/frontline-team-options?view=o365-worldwide).
2. **Define Shifts capabilities for your frontline**.

   If you created your teams through the deploy frontline dynamic teams at scale experience, you can choose to [deploy Shifts to your frontline teams at scale](https://learn.microsoft.com/en-us/microsoft-365/frontline/deploy-shifts-at-scale?view=o365-worldwide) in the Teams admin center. By doing so, you can standardize Shifts settings across all your frontline teams and manage them centrally. You select which capabilities to turn on or off and create schedule groups and time-off reasons that are set uniformly across all your frontline teams.

   Alternatively, you can use the [Create or replace schedule](https://learn.microsoft.com/en-us/graph/api/team-put-schedule?view=graph-rest-1.0&tabs=http) Graph API to define Shifts settings for your frontline teams and the [shiftsRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/shiftsroledefinition?view=graph-rest-beta) Graph API to [manage permissions to Shifts capabilities for your frontline managers](https://learn.microsoft.com/en-us/microsoft-365/frontline/manage-shifts-permissions-frontline-managers?view=o365-worldwide).

Note

Optionally, [set up a frontline operational hierarchy](https://learn.microsoft.com/en-us/microsoft-365/frontline/deploy-frontline-operational-hierarchy?view=o365-worldwide) to map your organization's structure of frontline teams and locations to a hierarchy in the Teams admin center. Creating a frontline operational hierarchy will enable [location scenarios](https://learn.microsoft.com/en-us/microsoft-365/frontline/set-up-open-shifts-across-locations?view=o365-worldwide) and other capabilities for your frontline.

## Shifts capabilities

Here's an overview of what frontline managers and workers can do in Shifts.

| Frontline manager capabilities | Standalone | Microsoft managed Shifts connector |
| --- | --- | --- |
| Create a schedule for their team.  <br>Supported methods:<br><br>- Manually create shifts and time off one by one.<br>- Bulk creation of shifts and time off through Excel import and copy/paste. | Yes | Not available in Shifts.<sup>1</sup> |
| Create open shifts for workers on their own team to request.  <br>Supported methods:<br><br>- Manually create shifts and time off one by one.<br>- Bulk creation of shifts and time off through Excel import and copy/paste. | Yes | Not available in Shifts.<sup>1</sup> |
| Create open shifts for workers on other teams \(locations\) to request. \(Preview\)  <br>Supported methods:<br><br>- Manually create shifts and time off one by one.<br>- Bulk creation of shifts and time off through Excel import and copy/paste. | Yes | No |
| Update and delete shifts, time off, and open shifts.  <br>Only manual one-by-one changes are supported. | Yes | Not available in Shifts.<sup>1</sup> |
| Manage Shifts settings for the team. | Yes<sup>2</sup> | No<sup>3</sup> |
| Create schedule groups to organize workers based on common characteristics within a team. For example, department or job type. | Yes | No<sup>4</sup> |
| Retrieve time sheet reports. | Yes | Yes |
| Retrieve the totals for hours worked and time off. | Yes | Yes |
| Manage requests from workers. | Yes | Yes |

<sup>1</sup>Creating, updating, and deleting shifts, time off, and open shifts are actions that frontline managers must do in the WFM system. The data is automatically synced to Shifts through the Shifts connector.  
<sup>2</sup>Depends on how your organization deployed Shifts. This might not be available for the frontline managers to manage locally.  
<sup>3</sup>Automatically configured when you set up the connection between your WFM system and the Shifts connector. No action is needed by frontline managers.  
<sup>4</sup>Automatically created based on the configuration of your WFM system.

| Frontline worker capabilities | Standalone | Microsoft managed Shifts connector |
| --- | --- | --- |
| View their own and their team's schedule. | Yes | Yes |
| View open shifts available in their schedule groups. | Yes | Yes |
| Request open shifts at their own location for manager's approval. | Yes | Yes<sup>1</sup> |
| Request open shifts at other locations for manager's approval at that location. \(Preview\) | Yes | No |
| Request time off. Currently, after the request is approved by a manager, the time off applies only to the team in which the worker requested it. | Yes | Yes<sup>1</sup> |
| Request to swap a shift with a coworker on the same team. | Yes | Yes<sup>1</sup> |
| Request to offer a shift to a coworker on the same team. | Yes | Yes<sup>1</sup> |
| Clock in and out of shifts and breaks. | Yes | Yes<sup>1</sup> |
| Edit timecard entries for clock in/out and breaks on mobile. | Yes | Yes |

<sup>1</sup>Validations are made to ensure rules and business logic from your WFM system are applied.

## Extend Shifts capabilities

Use the following resources to extend Shifts capabilities for your frontline workforce.

| Resource | Example scenario | Target apps |
| --- | --- | --- |
| [shift Graph API](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) | Your organization wants to create reports based on Shifts scheduling data. | Apps that want to read/write Shifts data. |
| [Graph API change notifications](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview?view=graph-rest-1.0) | Your organization doesn't require frontline managers' approval for open shift requests. You can use Shifts webhooks notifications to trigger the approval automation process for open shift requests. | Apps that read Shifts data and want to be notified about changes made in Shifts. Additionally, these apps aren't data owners and don't have additional validation to run. |
| [Shifts + Power Automate](https://make.powerautomate.com/connectors/shared_shifts/shifts-for-microsoft-teams/) | Your organization wants to take information from Shifts and create custom workflows with other apps and services. For example, create a flow to automatically approve swap shift requests and receive email notifications. | [Learn more](https://learn.microsoft.com/en-us/connectors/shifts). |

## Shifts resources

|  |  |
| --- | --- |
| ![](https://learn.microsoft.com/en-us/office/media/icons/deploy-teams.png) | **[Deploy Shifts at scale](https://learn.microsoft.com/en-us/microsoft-365/frontline/deploy-shifts-at-scale?view=o365-worldwide)** Configure and manage Shifts settings centrally in the Teams admin center and deploy Shifts to your frontline teams at scale. |
| ![](https://learn.microsoft.com/en-us/office/media/icons/administrator-teams.png) | **[Manage Shifts](https://learn.microsoft.com/en-us/microsoftteams/expand-teams-across-your-org/shifts/manage-the-shifts-app-for-your-organization-in-teams?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)** Get an overview of how to manage Shifts for your organization. Learn how to control access to Shifts, pin Shifts to the Teams app bar for easy access, enable shift-based tags, and more. |
| ![](https://learn.microsoft.com/en-us/office/media/icons/users-group.png) | **[Use roles to define your frontline managers and workers in Shifts](https://learn.microsoft.com/en-us/microsoft-365/frontline/shifts-frontline-manager-worker-roles?view=o365-worldwide)** Learn how to use team owner and team member roles in Teams and the schedule owner role in Shifts to define your frontline managers and workers in Shifts. |
| ![](https://learn.microsoft.com/en-us/office/media/icons/api-teams.png) | **[Manage Shifts permissions for frontline managers](https://learn.microsoft.com/en-us/microsoft-365/frontline/manage-shifts-permissions-frontline-managers?view=o365-worldwide)** Learn how to control the Shifts capabilities that are available to frontline managers for managing their team schedules, such as the Shifts settings that they can configure and whether they can create and manage schedule groups. |
| ![](https://learn.microsoft.com/en-us/office/media/icons/calendar-teams.png) | **[Set up open shifts across locations in Shifts for your frontline](https://learn.microsoft.com/en-us/microsoft-365/frontline/set-up-open-shifts-across-locations?view=o365-worldwide)** \(Preview\) With this feature, your frontline managers can offer open shifts across multiple locations \(teams\) within an area for workers to request and workers can see and request open shifts that are available at other locations. |
| ![](https://learn.microsoft.com/en-us/office/media/icons/help.png) | **[Shifts data FAQ](https://learn.microsoft.com/en-us/microsoftteams/expand-teams-across-your-org/shifts/shifts-data-faq?bc=/microsoft-365/frontline/breadcrumb/toc.json&toc=/microsoft-365/frontline/toc.json)** Learn where Shifts data is stored and other information related to Shifts data, including retention, retrieval, and encryption. |
| ![](https://learn.microsoft.com/en-us/office/media/icons/connector-teams.png) | **[Shifts connectors overview](https://learn.microsoft.com/en-us/microsoft-365/frontline/shifts-connectors?view=o365-worldwide)** Get an overview of Shifts connectors and how they work. Learn about the managed connectors that are available and the supported WFM systems. |
| ![](https://learn.microsoft.com/en-us/office/media/icons/connector-teams.png) | **[Reflexis Shifts connector for Microsoft Teams](https://learn.microsoft.com/en-us/microsoft-365/frontline/shifts-connectors?view=o365-worldwide#reflexis-shifts-connector-for-microsoft-teams)** Learn about integrating Shifts with the Reflexis WFM system through the connector. |
| ![](https://learn.microsoft.com/en-us/office/media/icons/connector-teams.png) | **[Create a custom integration to sync your workforce management system with Shifts](https://learn.microsoft.com/en-us/microsoft-365/frontline/shifts-custom-wfm-integration?view=o365-worldwide)** Learn how to create a custom solution to integrate Shifts with your WFM system using the Microsoft Graph API. |

## End user help and training

|  |  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| ![](https://learn.microsoft.com/en-us/office/media/icons/arrow-right-2-teams.png) | [Shifts end user documentation](https://support.microsoft.com/office/get-started-in-shifts-5f3e30d8-1821-4904-be26-c3cd25a497d6) | ![](https://learn.microsoft.com/en-us/office/media/icons/get-started-teams.png) | [Video: What is Shifts?](https://support.office.com/article/what-is-shifts-f8efe6e4-ddb3-4d23-b81b-bb812296b821) | ![](https://learn.microsoft.com/en-us/office/media/icons/calendar.png) | [Video: Create a shifts schedule](https://support.microsoft.com/office/create-a-shifts-schedule-2b94ca38-36db-4a1c-8fee-f8f0fec9a984) | ![](https://learn.microsoft.com/en-us/office/media/icons/blocks-teams.png) | [Video: Manage a Shifts schedule](https://support.microsoft.com/office/manage-and-view-a-shifts-schedule-63acda7b-ea39-441a-b1c6-c404a72e79f7) |  |
