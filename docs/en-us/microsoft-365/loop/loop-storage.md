<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Overview of Loop storage

Note

Loop My workspace shares a single user-owned SharePoint Embedded container with Copilot Pages and Copilot Notebooks. In the SharePoint admin center, PowerShell, and Purview audit data, this container's **application name is always `Loop`**. Loop is the application identity for the container even when it only stores Copilot Pages or Copilot Notebooks.

## At a glance

| Key fact | Details |
| --- | --- |
| **Storage locations** | SharePoint Embedded, SharePoint sites, or OneDrive \(depends on where content is created\) |
| **Personal SharePoint Embedded container control** | Disable both Loop workspace creation and Copilot Pages/Notebooks creation to prevent the single user-owned container from being created |
| **Quota** | Counts against your organization's SharePoint storage quota |
| **Container limit** | 25 TB maximum per container |
| **User departure** | Personal workspace follows the OneDrive deletion lifecycle; one manual handoff step at departure \(no automatic notification\), plus optional permanent reassignment. See [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide#options-when-a-user-leaves-the-organization) |

## Quick storage reference

Use this simplified view to quickly identify where content is stored:

| Created in... | Stored in... |
| --- | --- |
| **Loop app** \(any workspace\) | SharePoint Embedded containers |
| **Teams chat notes** | SharePoint Embedded containers |
| **Teams private** chat or meeting | User's OneDrive |
| **Teams channel** or channel meeting | SharePoint site \(channel folder or Meetings\) |
| **Outlook, OneNote, Whiteboard** | User's OneDrive |

## Storage

Loop content is stored in SharePoint, OneDrive, and [SharePoint Embedded](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/consuming-tenant-admin/cta). For Copilot Pages and Copilot Notebooks storage details, see [Storage for Copilot Pages and Copilot Notebooks](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide). Where the content was originally created determines its storage location. Use the table below to understand storage locations and lifetime management for each content type:

| Content originally created in | Content stored in SharePoint Embedded | Content stored in SharePoint Site | Content stored in User's OneDrive | Lifetime Management |
| --- | --- | --- | --- | --- |
| Loop application, My workspace \* | ✔️in user-owned container |  |  | user account |
| Loop application, shared workspace | ✔️in shared container |  |  | workspace owners |
| Teams [channel workspace](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/collaborate-in-real-time-with-workspaces-in-teams/4414334) | ✔️in shared container |  |  | Microsoft 365 Group |
| Teams [chat notes](https://support.microsoft.com/office/use-collaborative-notes-in-microsoft-teams-chats-6f19dd1f-b37a-47a2-9795-bb5deb4d0f58) | ✔️in container |  |  | Microsoft Teams Chat |
| Teams channel meeting |  | ✔️in 📁`Meetings` |  | Microsoft 365 Group |
| Teams channel |  | ✔️in Channel folder |  | Microsoft 365 Group |
| Teams private chat |  |  | ✔️in 📁`Microsoft Teams Chat files` | user account |
| Teams private meeting |  |  | ✔️in 📁`Meetings` | user account |
| Outlook email |  |  | ✔️in 📁`Attachments` | user account |
| OneNote for Windows or for the web |  |  | ✔️in 📁`OneNote Loop files` | user account |
| Whiteboard |  |  | ✔️in 📁`Whiteboard\\Components` | user account |

\* The My workspace SharePoint Embedded container is the same physical user-owned container used by Copilot Pages and Copilot Notebooks.

## User-owned container name

Copilot Pages and Copilot Notebooks use the same user-owned SharePoint Embedded container as Loop My workspace. This container is named 'Pages' if the person visits the Microsoft Copilot app first. It is named 'My workspace' \(localized into the language of the user's Loop experience during creation\) if the person visits the Loop application first. Refer to [listing all user-owned containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide#listing-all-the-user-owned-containers) to get a list, regardless of the container name.

This single user-owned container is created when a user first needs one of these experiences and at least one of the relevant creation policies allows it. If *Create Loop workspaces in Loop* is disabled but *Create and view Copilot Pages and Copilot Notebooks* is enabled, creating a Copilot Page or Notebook can still create the container. If *Create and view Copilot Pages and Copilot Notebooks* is disabled but *Create Loop workspaces in Loop* is enabled, opening Loop My workspace can still create that same container.

To prevent the single user-owned container from being created, disable both of the following policies for the same user:

1. *Create and view Copilot Pages and Copilot Notebooks*
2. *Create Loop workspaces in Loop*

For more information, see the admin policies articles for [Loop](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide) and [Copilot Pages and Copilot Notebooks](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide).

## Storage quota

All Loop workspaces count against your organization's SharePoint storage quota.

SharePoint Embedded also offers a platform for developers to build their own applications. This alternate usage pattern which bills per use is different from Loop and Copilot Pages storage quota management.

## Storage limits

Loop workspaces have a maximum size of 25 TB. This limit can't be increased or decreased. Learn more about [SharePoint Embedded container limits](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/limits-calling).

## Storage management after user departure

### Types of Loop workspaces

Storage behaviors after user departure depends on the type of Loop workspace. There's one **personal workspace** per user in your organization, created on demand by the person when accessed. All other created Loop workspaces are **shared workspaces**. For more information, see [workspace membership and Microsoft 365 Groups](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-permission?view=o365-worldwide#workspace-membership-and-microsoft-365-groups) on the two shared workspace types.

### Shared Workspaces

#### Tenant-owned

- A roster permissions tenant-owned shared Loop workspaces. If all owners leave the company, the workspace becomes ownerless, remains in the tenant, and isn't automatically deleted.
- You must be an owner to delete a workspace. If all the owners left the company, members can't delete the workspace until an IT administrator adds new owners.

#### Microsoft 365 Group-owned

- The Microsoft 365 Group permissions and manages the lifetime of group-owned shared Loop workspaces, similar to the management of SharePoint Team sites.

### Personal Workspaces

- Copilot Pages, Copilot Notebooks, and [My workspace](#my-workspace) store content within the same physical user-owned SharePoint Embedded container.
- This personal content is private by default, allowing users to work without forced sharing or coauthoring, similar to OneDrive.

#### My workspace

- My workspace is stored in the same user-owned SharePoint Embedded container, created through Loop application IDs. The container's lifecycle is tied to its [principal owner](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/consuming-tenant-admin/ctaux#active-containers)—the user the container belongs to. When the principal owner's account is deleted, the container is scheduled for deletion.
- When a user leaves, the container follows the same OneDrive deletion lifecycle, with one manual handoff step at departure \(access and notification aren't automatic\) and the option to permanently reassign the container to a new owner. For the full process, options, and comparison with OneDrive, see [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide#options-when-a-user-leaves-the-organization).

#### Ideas

- The Ideas workspace is deprecated, no longer created by default, and replaced with the My workspace personal workspace.
- Ideas were the first default workspace, was tenant-owned, permissioned with a single-person roster.
- The Loop application doesn't delete the deprecated Ideas workspace; a user or an admin must delete it if needed.
- If a user doesn't have multiple owners on their Ideas workspace, the workspace becomes ownerless when they leave the company. It remains in the tenant and isn't automatically deleted.

### Loop components created in Microsoft 365 outside of the Loop application or Copilot Pages

See [Storage](#storage). When content is stored in OneDrive, if that user leaves the organization, the standard OneDrive IT policy is applied. When content is stored in SharePoint, the standard SharePoint IT policy is applied. Learn more about [OneDrive and SharePoint Retention and Deletion](https://learn.microsoft.com/en-us/sharepoint/retention-and-deletion).

## Related articles

- [Summary of compliance, lifecycle, governance](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-compliance-summary?view=o365-worldwide)
- [Requirements](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-requirements?view=o365-worldwide)
- [Permissions](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-permission?view=o365-worldwide)
- [Admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide)
- [UX examples for admin policy states](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-ux-examples?view=o365-worldwide)
- [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
- [Purview management](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide)
- [Overview of Loop components in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-components-teams?view=o365-worldwide)
- [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide)
