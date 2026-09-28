<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Admin policies for Copilot Pages and Copilot Notebooks

Copilot Pages \(`.page` files\) and Copilot Notebooks are stored in the same user-owned SharePoint Embedded container used by Loop My workspace. In the SharePoint admin center, PowerShell, and Purview audit data, this container always appears with an application name of `Loop` — there's no separate Copilot Pages or Copilot Notebooks application filter. Storage counts toward your organization's overall SharePoint quota. For full details, see [storage and lifecycle](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide). IT administrators can control creation and use of Copilot Pages and Copilot Notebooks through Cloud Policy settings.

## At a glance

| What you want to control | Where to configure | Default |
| --- | --- | --- |
| **Copilot Pages and Copilot Notebooks creation** | Cloud Policy: *Create and view Copilot Pages and Copilot Notebooks* | Enabled |
| **Code previews in Copilot Chat and Copilot Pages** | Cloud Policy: *Enable code previews for AI-generated content in Microsoft Copilot Chat and Copilot Pages* | Enabled |

Tip

**Quick reference scenarios**

- **Block Loop but allow Copilot Pages/Notebooks**: Disable Loop policies; leave *Create and view Copilot Pages and Copilot Notebooks* enabled. The same user-owned container can still be created by Copilot Pages or Copilot Notebooks.
- **Block Copilot Pages/Notebooks but allow Loop**: Disable *Create and view Copilot Pages and Copilot Notebooks*; leave Loop policies enabled. The same user-owned container can still be created by Loop My workspace.
- **Block everything**: Disable both policies
- **Block code previews only**: Disable *Enable code previews for AI-generated content in Microsoft Copilot Chat and Copilot Pages*; leave *Create and view Copilot Pages and Copilot Notebooks* enabled

## Requirements

Copilot Pages and Copilot Notebooks are a core service integrated into SharePoint and Microsoft 365. See [requirements](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-requirements?view=o365-worldwide) to learn more about configuration requirements, service connections, and license requirements.

To apply Cloud Policy to specific users instead of the entire tenant, see [Scoping Cloud Policy with Microsoft 365 Groups](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide#scoping-cloud-policy-with-microsoft-365-groups). You can also apply Cloud Policy using security or dynamic groups, see [Create, edit, or delete a security group](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-edit-or-delete-a-security-group) and [Create dynamic groups in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/use-dynamic-groups). If you apply the policy to all users in the tenant, group setup isn't required.

## Relationship to Loop components

Copilot Pages and Copilot Notebooks are independent of Loop. You can enable or disable them separately. They do share a single user-owned SharePoint Embedded container with Loop My workspace, which has implications for the **Create and view Copilot Pages and Copilot Notebooks** policy:

- The shared container is created when *either* the Copilot Pages and Copilot Notebooks policy *or* the Loop **Create Loop workspaces in Loop** policy allows creation for the user. To prevent the container from being created, disable both policies for the same user.
- See [storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide) for the full explanation of the shared container, including naming and lifecycle.

To share Copilot Pages as interactive components \(instead of just hyperlinks\) in Teams, Outlook, Whiteboard, OneNote, or the Loop application, Loop components must be enabled. Without Loop components enabled in the Microsoft 365 ecosystem, Copilot Pages are only interactive within the Microsoft Copilot app and supported chat experiences. For details on enabling Loop components in the Microsoft 365 ecosystem, see [Loop admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide).

## User experience when Copilot Pages and Copilot Notebooks are disabled

When creation is disabled, users are unable to create new Copilot Pages or Notebooks. The Pages module is visible in the Microsoft Copilot app, but the Notebooks module is hidden, preventing users from accessing existing Notebooks through the Copilot App. If Loop My workspace is still enabled for the user, the same user-owned container might still exist or be created by Loop.

Existing Copilot Pages and Notebooks aren't deleted. Users can still view and edit existing items if they have permission. These files remain accessible in the following ways:

- **Loop application**: For viewing and editing Pages
- **Microsoft Copilot app**: For accessing items created in chat experiences
- **Original storage locations**: Files added to Notebooks remain available in OneDrive and SharePoint where they're stored

Existing items are also discoverable through search, Purview, and admins can export them.

Important

Sharing links to Copilot Notebooks don't work when creation is disabled via the policy in this article.

## Settings management in Cloud Policy

Copilot Pages and Copilot Notebooks check the following [Cloud Policy](https://learn.microsoft.com/en-us/deployoffice/admincenter/overview-cloud-policy) settings:

- **Create and view Copilot Pages and Copilot Notebooks**
- **Enable code previews for AI-generated content in Microsoft Copilot Chat and Copilot Pages**

1. Sign in to [https://config.office.com/](https://config.office.com/) with your Microsoft 365 admin credentials.
2. Select **Customization** from the left pane.
3. Select **Policy Management**.
4. Create a new policy configuration or edit an existing one.
5. From the **Choose the scope** dropdown list, choose either **All users** or select the group for which you want to apply the policy. For more information, see [Scoping Cloud Policy with Microsoft 365 Groups](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide#scoping-cloud-policy-with-microsoft-365-groups).
6. In **Configure Settings**, choose one of the following settings:

   - For **Create and view Copilot Pages and Copilot Notebooks**

     - **Enabled**: Copilot Pages and Copilot Notebooks creation and integration are available to the users.
     - **Disabled**: Copilot Pages and Copilot Notebooks creation and integration aren't available to the users.
     - **Not configured**: Copilot Pages and Copilot Notebooks creation and integration are available to the users.

       Note

       If your organization [disabled the creation of OneDrive](https://learn.microsoft.com/en-us/sharepoint/manage-user-profiles#disable-onedrive-creation-for-some-users), regardless of the setting noted here, these people in your organization can't create Copilot Pages or Copilot Notebooks.

   - For **Enable code previews for AI-generated content in Microsoft Copilot Chat and Copilot Pages**

     - **Enabled**: Users can view and interact with AI-generated code previews in Copilot Chat and Copilot Pages, including building [lightweight apps](https://support.microsoft.com/topic/fd42d9f3-258e-4bf9-8c5e-a73083a197cc).
     - **Disabled**: Copilot doesn't run code previews in Copilot Chat or Copilot Pages.
     - **Not configured**: Users can view and interact with AI-generated code previews in Copilot Chat and Copilot Pages, including building [lightweight apps](https://support.microsoft.com/topic/fd42d9f3-258e-4bf9-8c5e-a73083a197cc).

7. Save the policy configuration.
8. Reassign priority for any security group, if required. \(If two or more policy configurations are applicable to the same set of users, the one with the higher priority is applied.\)

   In case you create a new policy configuration or change the configuration for an existing policy, there can be a delay in the change being reflected:

   - If there were existing policy configurations before the change, the change takes up to 90 minutes to be reflected.
   - If there were no policy configurations before the change, the change takes up to 24 hours to be reflected.

### Enable a policy for a subset of users

To enable a Cloud Policy for only some users:

1. Create **Group A** containing the users you want to enable the policy for. Assign the Cloud Policy to this group and set it to **Enabled**.
2. Create **Group B** that includes **All users**. Assign the same Cloud Policy to this group and set it to **Disabled**.
3. Set the priority for **Group A** to a lower number \(for example, priority 0\) so it's evaluated before **Group B** \(for example, priority 1\).

In Cloud Policy, lower priority numbers are evaluated first. With this configuration, users in **Group A** get the policy **Enabled**, while all other users in **Group B** get it **Disabled**.

To do the reverse — *disable* the policy for a specific group and leave it *enabled* for everyone else — use the same two-group pattern with the **Enabled** and **Disabled** values swapped: set **Group A** \(the targeted users\) to **Disabled** at the lower priority, and **Group B** \(All users\) to **Enabled** at the higher priority.

## Related articles

- [Get started with Microsoft Copilot Pages](https://support.microsoft.com/en-us/topic/get-started-with-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f)
- [Build lightweight apps within Microsoft Copilot Pages](https://support.microsoft.com/en-us/topic/build-lightweight-apps-within-microsoft-365-copilot-pages-fd42d9f3-258e-4bf9-8c5e-a73083a197cc)
- [Summary of compliance, lifecycle, governance](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-compliance-summary?view=o365-worldwide)
- [Requirements](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-requirements?view=o365-worldwide)
- [Storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide)
- [Permissions](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-permission?view=o365-worldwide)
- [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
- [Purview management](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide)
