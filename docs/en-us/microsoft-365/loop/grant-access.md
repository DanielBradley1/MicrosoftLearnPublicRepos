<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Grant access to Copilot Pages, Copilot Notebooks, and Loop containers

Copilot Pages, Copilot Notebooks, and Loop workspaces are stored in [SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide). These containers come in three ownership types:

- **User-owned**: A single container per user that holds their Copilot Pages, Copilot Notebooks, and Loop My workspace content.
- **Tenant-owned**: Shared Loop workspaces created by users within the organization.
- **Group-owned**: Loop workspaces associated with a Microsoft 365 Group, such as Teams channel workspaces.

For more information on container types and how to manage them, see [Manage SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide).

When a user leaves, a user-owned container follows the same [OneDrive deletion lifecycle](https://learn.microsoft.com/en-us/sharepoint/retention-and-deletion#the-onedrive-deletion-process) as the rest of Microsoft 365, with one manual handoff step at departure and the option to permanently reassign the container to a new owner. For an overview of your choices, see [Options when a user leaves the organization](#options-when-a-user-leaves-the-organization).

Use this workflow when you need to add owners to a container, for example:

- **User departure**: Preserve or reassign a user-owned container when its owner leaves the organization. See [Options when a user leaves the organization](#options-when-a-user-leaves-the-organization).
- **Owner unavailability**: Add new owners to help manage a container when the current owner is unavailable, such as during extended leave.
- **Ownerless workspaces**: Assign owners to tenant-owned workspaces that are [ownerless](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide#ownerless-workspaces) after all owners left the organization.
- **IT investigation or audit**: Grant access to review content for compliance, legal, or security purposes.
- **Data management**: Allow a designated person to review and organize content as part of a governance workflow.

Note

For tenant-owned Loop workspaces created before April 2025, see [Tenant-owned workspaces](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide#tenant-owned-workspaces) for membership guidance.

Important

For user departure scenarios, content must be **copied** to a new location before the original container is deleted. Links to the original container stop working after deletion.

## Options when a user leaves the organization

A user-owned container's lifecycle is tied to its principal owner and follows the same [OneDrive deletion lifecycle](https://learn.microsoft.com/en-us/sharepoint/retention-and-deletion#the-onedrive-deletion-process) as the rest of Microsoft 365: after the user account is deleted, the container stays active for a configurable retention period, moves to the recycle bin for a period, and is then permanently deleted. A single control governs both OneDrive and user-owned containers, so the configured retention period applies the same lifetime to both, and admins can recover a deleted container during the recycle bin period.

The one difference from OneDrive is the handoff at departure. OneDrive [automatically delegates access to the user's manager](https://learn.microsoft.com/en-us/sharepoint/retention-and-deletion#configure-automatic-access-delegation) and emails them. A user-owned container has no automatic delegation or notification, so the IT admin completes that one step manually. Everything after the handoff—retention, recycle bin, and deletion—is identical to OneDrive.

Important

Because the handoff isn't automatic, it's easy to miss. If no one is granted access and notified before the retention period ends, the content is permanently deleted. Large organizations can automate this step by using PowerShell to grant access and Power Automate to send the notification; smaller organizations should add it to their offboarding checklist.

You have two ways to handle a departing user's container:

- **Preserve content \(works like OneDrive\).** Add a custodian as an owner, then notify them with the container link so they can copy what needs to be kept before the container is deleted. This mirrors OneDrive offboarding, with the access grant and notification done manually instead of automatically. The rest of this article describes this option in detail, starting with [Locate the container](#locate-the-container).
- **Reassign the container to a new owner \(not available for OneDrive\).** Permanently transfer the entire container to a different user with the SharePoint Embedded [principal owner transfer](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spocontainer#principalownertransfer) capability in PowerShell, which is supported only for user-owned containers. The new user becomes the principal owner, which resets the deletion schedule to their account and removes the container from the previous owner's schedule. Notify them with the container link as described in [Notify the new owner](#notify-the-new-owner).

For a side-by-side comparison, see [How this workflow compares to OneDrive offboarding](#how-this-workflow-compares-to-onedrive-offboarding).

## Prerequisites

- [SharePoint Embedded administrator role](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/adminrole)
- Access to the [SharePoint admin center](https://go.microsoft.com/fwlink/?linkid=2185219)

## Locate the container

![Screenshot showing the Active containers list in the SharePoint admin center filtered to Loop containers.](https://learn.microsoft.com/en-us/microsoft-365/loop/media/spe-admin-active-containers.png?view=o365-worldwide)

1. Go to the **SharePoint admin center**.
2. Expand **SharePoint Embedded**, and then select **Active containers**.
3. Filter by **Application name: Loop**. Optionally, filter by **Ownership type** \(User, Tenant, or Group\) to narrow the results.

   Note

   Copilot Pages, Copilot Notebooks, and Loop workspace containers all appear under **Application name: Loop**, because they share the same SharePoint Embedded application identity. There's no separate Copilot Pages or Copilot Notebooks filter.
4. Search for the container by name or filter by **Principal owner**. The user-owned container might be named "Pages" or "My workspace" depending on whether the user visited the Microsoft Copilot app or the Loop app first. For more information, see [container name](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide#container-name).
5. Select the container.

## Add a custodian as an owner

![Screenshot showing the Add owner dialog in the container details panel of the SharePoint admin center.](https://learn.microsoft.com/en-us/microsoft-365/loop/media/spe-admin-add-owner.png?view=o365-worldwide)

1. In the container details panel, on the **Membership** tab, select **Add owner**.
2. Search for the person you want to add \(typically the user's manager, a designated reviewer, or a team member\).
3. Confirm the assignment.

Adding an owner grants access to all content in the container but doesn't change the [principal owner](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/consuming-tenant-admin/ctaux#active-containers)—the user the container belongs to. When the principal owner's account is deleted, the container is scheduled for deletion. You can revoke access at any time by removing the additional owners. To permanently reassign the container to a different user instead of preserving and copying content, use principal owner transfer \(see [Options when a user leaves the organization](#options-when-a-user-leaves-the-organization)\).

## Copy the Container Redirect URL

![Screenshot showing the Container Redirect URL field in the General tab of the container details panel.](https://learn.microsoft.com/en-us/microsoft-365/loop/media/spe-admin-container-redirect-url.png?view=o365-worldwide)

1. In the container details panel, on the **General** tab, locate the **Container Redirect URL** field.
2. Copy the full URL \(select all the text, then press Ctrl+C or use the right-click menu\).

The Container Redirect URL is a clickable link that opens the container in the Loop app for any user who has access. Send this URL to the new owner so they can access the content.

## Notify the new owner

Send the new owner a message with the Container Redirect URL. Choose the appropriate template based on your scenario.

**General access \(tenant-owned or group-owned containers\)**: Use this template when granting access to a shared Loop workspace:

```text
Subject: You have access to a Loop workspace

You've been added as an owner of the [Workspace Name] Loop
workspace. Open the workspace using this link:

[Container Redirect URL]
```

**User departure \(user-owned containers\)**: Use this template when a user left the organization and their container is scheduled for deletion:

```text
Subject: Action required: Review and save content from [User]

You've been added as an owner of [User]'s personal container,
which holds their Copilot Pages, Copilot Notebooks, and Loop
My workspace content. This container will be deleted after the
retention period that follows the user's account removal from
the organization.

Review and copy any content that needs to be retained before
then:

[Container Redirect URL]

Copy any required content to a new Copilot Notebook or Loop
workspace. Content that isn't copied will be permanently
deleted.
```

## Preserve Copilot Pages and Loop content

![Screenshot showing the Assigned section in the Loop navigation bar with the content list in the center pane.](https://learn.microsoft.com/en-us/microsoft-365/loop/media/loop-assigned-content-list.png?view=o365-worldwide)

When the new owner opens the Container Redirect URL, an **Assigned** entry appears in the Loop navigation bar on the left. Selecting it displays a list of the user's My workspace and any Copilot Notebooks in the center pane.

To preserve Copilot Pages or Loop pages:

1. In the center pane, select **Pages** or **My workspace**. The list navigates in place to show the My workspace contents.
2. Select the page you want to preserve. The page renders in the right pane.
3. Right-click the page in the list and select **Copy to workspace**.

   ![Screenshot showing the right-click context menu on a page with the Copy option highlighted.](https://learn.microsoft.com/en-us/microsoft-365/loop/media/loop-copy-page-context-menu.png?view=o365-worldwide)
4. Choose a destination \(another Loop workspace\).

To return to the list of My workspace and Copilot Notebooks, use the back navigation, or choose the Assigned entry in the Loop navigation bar.

## Preserve Copilot Notebook content

![Screenshot showing a Copilot Notebook open from the Assigned content list.](https://learn.microsoft.com/en-us/microsoft-365/loop/media/cpcn-assigned-notebook-open.png?view=o365-worldwide)

From the **Assigned** content list, select a Copilot Notebook. The notebook opens in a new browser tab in the Microsoft Copilot app.

Copilot Notebooks contain several types of content. Before you start, review the notebook to identify what needs to be preserved:

| Content type | Where it's stored | Preservation action |
| --- | --- | --- |
| **Copilot Pages** \(items without a hyperlink overlay in the navigation bar\) | SharePoint Embedded container | Select **Preserve** on each page you need to preserve |
| **Overview content** \(Key Insights, Summary\) | SharePoint Embedded container | Select and copy the text manually, then paste it into a suitable destination |
| **Copilot Instructions** \(custom instructions\) | SharePoint Embedded container | Copy the text manually and re-create in the new notebook |
| **References** \(items with a hyperlink overlay\) | Original source location \(not at risk\) | Open each reference, copy the URL from the browser address bar, and add it to the new notebook |
| **Chat conversations** | Not stored in the container | Can't be preserved or copied |

Referenced files \(items with a hyperlink overlay in the References section\) are stored in their original location and aren't deleted when the container is deleted. Only the organized collection of links in the notebook is lost.

### Re-create a Copilot Notebook

There's no bulk workflow for transferring a Copilot Notebook to a new owner. To re-create a notebook, the new owner works through the content manually. A side-by-side window layout with the original notebook and the new one both visible can make this process easier to follow.

1. [Create a new Copilot Notebook](https://support.microsoft.com/topic/0775e693-11c6-4d80-8aba-fcc81a737a06).
2. [Share the new notebook](https://support.microsoft.com/topic/e8faaac5-4976-402d-b0a3-ea61f01555ff) with the same people. Open the sharing dialog of the original notebook to see who has access, then add each person to the new notebook.
3. [Add references](https://support.microsoft.com/topic/73048ee1-fd1d-4f7b-b850-b011029e09f2) from the original notebook. Open each reference to load it in a new tab, copy the URL from the browser address bar, and add it as a reference in the new notebook. Repeat for each reference.
4. Preserve Copilot Pages and overview content. Open each page in the original notebook and select **Preserve**, then add the preserved content to the new notebook.
5. Re-create [custom instructions](https://support.microsoft.com/topic/763a9536-d459-4f90-8835-c411863d91ce). Copy the text of the original instructions and paste it into the new notebook's custom instructions.

Important

In user departure scenarios, access alone doesn't preserve data. The new owner must copy or preserve content before the retention period expires.

## How this workflow compares to OneDrive offboarding

This workflow follows the same [OneDrive retention and deletion](https://learn.microsoft.com/en-us/sharepoint/retention-and-deletion) lifecycle, with two differences: the access handoff at departure is manual instead of automatic, and you can permanently reassign the container \(which OneDrive doesn't support\).

| Capability | OneDrive | Copilot Pages, Copilot Notebooks, and Loop My workspace |
| --- | --- | --- |
| **Automatic manager access** | Yes, [configured by default](https://learn.microsoft.com/en-us/sharepoint/retention-and-deletion#configure-automatic-access-delegation) | No, requires manual custodian assignment |
| **Retention period** | [Configurable](https://learn.microsoft.com/en-us/sharepoint/set-retention) | Same as OneDrive \(uses the same [retention setting](https://learn.microsoft.com/en-us/sharepoint/set-retention)\) |
| **Content transfer** | Move or copy files | Copy files |
| **Ownership reassignment** | Not supported \(move or copy files instead\) | Supported using the SharePoint Embedded [principal owner transfer](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spocontainer#principalownertransfer) capability |
| **Recycle bin recovery** | Admin can [restore deleted OneDrive](https://learn.microsoft.com/en-us/sharepoint/restore-deleted-onedrive) during the recycle bin period | Admin can [restore the deleted container](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/consuming-tenant-admin/ctaux#restore-a-container) during the recycle bin period |

For the full offboarding process for a user, including email, OneDrive, and device management, see [Remove a former user](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/remove-former-employee).

## Related articles

- [Storage for Copilot Pages and Copilot Notebooks](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide)
- [Storage for Loop](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide)
- [Manage SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
- [Purview management for SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide)
- [OneDrive retention and deletion](https://learn.microsoft.com/en-us/sharepoint/retention-and-deletion)
- [Remove a former user](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/remove-former-employee)
