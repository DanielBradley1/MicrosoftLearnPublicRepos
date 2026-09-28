<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Overview of Copilot Pages and Copilot Notebooks storage

Note

Copilot Pages and Copilot Notebooks are stored in a user-owned SharePoint Embedded container that is also used by Loop My workspace. In the SharePoint admin center, PowerShell, and Purview audit data, this container's **application name is always `Loop`** — even when it only stores Copilot Pages or Copilot Notebooks. There's no separate Copilot Pages or Copilot Notebooks application filter.

## At a glance

| Key fact | Details |
| --- | --- |
| **Storage location** | SharePoint Embedded \(user-owned container\) |
| **Container name** | "Pages" or "My workspace" \(depends on which app creates it first\) |
| **Creation control** | Disable both Loop and Copilot Pages/Notebooks creation policies to prevent the single user-owned container from being created |
| **Quota** | Counts against your organization's SharePoint storage quota |
| **Container limit** | 25 TB maximum |
| **User departure** | Follows the OneDrive deletion lifecycle; one manual handoff step at departure \(no automatic notification\), plus optional permanent reassignment. See [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide#options-when-a-user-leaves-the-organization) |
| **Recycle bin** | No end-user recycle bin for Copilot Notebooks |

## Storage

Copilot Pages and Copilot Notebooks are stored within your organization in SharePoint Embedded. Each user has a single user-owned container that stores Copilot Pages, Copilot Notebooks, and Loop My workspace content. The container is lifetime managed with the user account and can be [managed using SharePoint Embedded admin tools](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide).

## Container name

Copilot Pages, Copilot Notebooks, and Loop My workspace all use the same user-owned container. This container is named 'Pages' if the person visits the Microsoft Copilot app first. It is named 'My workspace' \(localized into the language of the user's Loop experience during creation\) if the person visits the Loop app first. Refer to [listing all user-owned containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide#listing-all-the-user-owned-containers) to get a list, regardless of the container name.

This single user-owned container is created when a user first needs one of these experiences and at least one of the relevant creation policies allows it. If *Create Loop workspaces in Loop* is disabled but *Create and view Copilot Pages and Copilot Notebooks* is enabled, creating a Copilot Page or Notebook can still create the container. If *Create and view Copilot Pages and Copilot Notebooks* is disabled but *Create Loop workspaces in Loop* is enabled, opening Loop My workspace can still create that same container.

To prevent the single user-owned container from being created, disable both policies for the same user.

## Storage quota

All Copilot Pages and Copilot Notebooks count against your organization's SharePoint storage quota.

SharePoint Embedded also offers a platform for developers to build their own applications. This alternate usage pattern, which bills per use, is different from Loop and Copilot Pages storage quota management.

## Storage limits

Copilot Pages + Copilot Notebooks container has a maximum size of 25 TB. This limit can't be increased or decreased. Learn more about [SharePoint Embedded container limits](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/limits-calling).

## Storage management after user departure

Copilot Pages and Copilot Notebooks are stored together in the same user-owned SharePoint Embedded container. This personal content is private by default, allowing users to work without forced sharing or coauthoring, similar to OneDrive.

The container's lifecycle is tied to its [principal owner](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/consuming-tenant-admin/ctaux#active-containers)—the user the container belongs to. When the principal owner's account is deleted, the container is scheduled for deletion.

When a user leaves, the container follows the same OneDrive deletion lifecycle, with one manual handoff step at departure \(access and notification aren't automatic\) and the option to permanently reassign the container to a new owner. For the full process, options, and comparison with OneDrive, see [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide#options-when-a-user-leaves-the-organization).

Important

There's no end-user recycle bin for Copilot Notebooks. Neither administrators nor end users can recover individually deleted Copilot Notebooks.

## Related articles

- [Summary of compliance, lifecycle, governance](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-compliance-summary?view=o365-worldwide)
- [Requirements](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-requirements?view=o365-worldwide)
- [Permissions](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-permission?view=o365-worldwide)
- [Admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide)
- [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
- [Purview management](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide)
- [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide)
