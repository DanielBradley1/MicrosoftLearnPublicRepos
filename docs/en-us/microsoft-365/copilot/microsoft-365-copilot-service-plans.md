<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-service-plans -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Microsoft Copilot service plan diagnostic tool and service plans for IT admins

Microsoft Copilot is an everyday AI tool that helps users with their work tasks, including tasks in their Microsoft 365 apps. To learn about Microsoft Copilot, see [What is Microsoft Copilot?](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview).

Microsoft Copilot has different features and capabilities that are available in the service plans associated with a Microsoft Copilot license. If users are missing functionality, it's possible the user is missing a service plan.

In the Microsoft 365 admin center, there's a diagnostic tool that shows the service plans assigned to a user account. The diagnostic tool uses the user's email address or user principal name \(UPN\) to identify and then list all the Microsoft Copilot service plans assigned.

This article shows you how to access & use the self-help diagnostic tool and lists the service plans that you see in the diagnostic tool. Use this information to troubleshoot missing Copilot functionality by checking if the issue is associated with a missing service plan.

This article applies to:

- Microsoft Copilot

## Prerequisites

To use the feature in this article, sign into the Microsoft 365 admin center with the following role-based access control \(RBAC\) role:

- AI administrator

To learn more, see [Admin roles in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles).

Tip

Microsoft recommends you sign in with the least privileged role that you need to complete your task. Typically, the Global Administrator role is too powerful for most tasks, including managing the Copilot feature described in this article.

## Step 1 - Run the diagnostic tool in the Microsoft 365 admin center

Admins can verify the service plans assigned to a user using the [Run Tests: Copilot Service Plan Diagnostic](https://aka.ms/PillarCopilotServicePlan) in the Microsoft 365 admin center.

The tool identifies and lists all the Microsoft Copilot service plans assigned.

1. Sign into the [Microsoft 365 admin center](https://admin.microsoft.com) as an AI administrator.
2. In the left navigation pane, select **Support** > **Help and support**.
3. In the prompt box, enter `copilot missing`. This step opens the diagnostic tool.

   Or, open the diagnostic tool directly at [Run Tests: Copilot Service Plan Diagnostic](https://aka.ms/PillarCopilotServicePlan).
4. Select **Run diagnostics** > Enter the email address or user principal name \(UPN\) of the user > **Run tests**.

The output identifies and lists all the Microsoft Copilot service plans assigned to the user.

## Step 2 - Review the Microsoft Copilot service plan names

The following table lists the service plan names you see in the diagnostic tool output.

If one of the following service plans isn't listed in the diagnostic output, then review the [Microsoft Copilot feature availability](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/microsoft-365-copilot#feature-availability). Check if the feature aligns with the missing Copilot functionality you're trying to verify.

| Feature & Service Plan name | Learn more |
| --- | --- |
| Microsoft Copilot Studio  <br>  <br>**Service plan name**: `Copilot Studio in Copilot for M365` | - [Copilot Studio overview](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-what-is-copilot-studio)  <br>- [Get access to Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/requirements-licensing-subscriptions) |
| Microsoft Graph Connectors  <br>  <br>**Service plan name**: `Graph Connectors in Microsoft 365 Copilot` | - [Build Microsoft Graph connectors for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-graph-connector)  <br>- [Custom Microsoft Graph connectors for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/publish) |
| Intelligent Search  <br>  <br>**Service plan name**: `Intelligent Search` | [Microsoft Copilot feature availability](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/microsoft-365-copilot#feature-availability) |
| Copilot in SharePoint - Includes SharePoint agents and a [rich text editor](https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/rich-text-editor-control).  <br>  <br>**Service plan name**: `Microsoft 365 Copilot for SharePoint` | - [Get started with SharePoint agents](https://support.microsoft.com/office/get-started-with-sharepoint-agents-69e2faf9-2c1e-4baa-8305-23e625021bcf)  <br>- [Authoring with Copilot in SharePoint: An overview](https://support.microsoft.com/topic/authoring-with-copilot-in-sharepoint-an-overview-a22514c9-7bc5-4c04-a599-455d573a1800)  <br>- [Copilot in SharePoint FAQ](https://support.microsoft.com/office/frequently-asked-questions-about-copilot-in-sharepoint-eb1b7668-3d98-4a93-98ef-f0c6dfc694f0) |
| Copilot in Microsoft Teams  <br>  <br>**Service plan name**: `Microsoft 365 Copilot in Microsoft Teams` | [Overview of AI in Microsoft Teams for IT admins](https://learn.microsoft.com/en-us/microsoftteams/copilot-ai-agents-overview)  <br>  <br> |
| Copilot in Microsoft 365 apps  <br>  <br>**Service plan name**: `Microsoft 365 Copilot in Productivity Apps` | [Copilot features in Microsoft 365 apps](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview#copilot-features-in-microsoft-365-apps) |
| Microsoft Copilot Chat - work  <br>  <br>**Service plan name**: `Microsoft Copilot with Graph-grounded chat` | - [Manage Microsoft Copilot Chat](https://learn.microsoft.com/en-us/copilot/manage)  <br>- [Which Copilot is right for me or my organization?](https://learn.microsoft.com/en-us/microsoft-365/copilot/which-copilot-for-your-organization) |
| Microsoft Copilot Power Platform connectors  <br>  <br>**Service plan name**: `Power Platform Connectors in Microsoft 365 Copilot` | - [Connectors overview](https://learn.microsoft.com/en-us/connectors/overview)  <br>- [Use Power Platform connectors in Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-connectors) |

## Common issues

- The diagnostic tool and the Microsoft 365 admin center can become unsynchronized. For example, the admin center shows a service plan assigned to a user, but the diagnostic tool shows that the service plan isn't assigned.

  This situation typically affects older user accounts with existing subscriptions and then new service plans are added to the subscription.

  To resolve the synchronization issue:

  1. In the [Microsoft 365 admin center](https://admin.microsoft.com), go to the affected user account and uncheck the associated service plans.
  2. Save your changes.
  3. Re-enable the service plan and save the changes.
  4. Rerun the diagnostic tool and verify that the service plan information is successfully synced.

- If the diagnostic output is missing a service plan \(listed in [Step 2 - Review the Microsoft Copilot service plan names](#step-2---review-the-microsoft-copilot-service-plan-names)\), then review the [Microsoft Copilot feature availability](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/microsoft-365-copilot#feature-availability) list.

  Then:

  - Verify that the Copilot feature is included in your license.
  - Assign the missing service plan to the user account.

## Related articles

- [Microsoft Copilot feature availability and service description](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/microsoft-365-copilot#feature-availability)
- [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview)
