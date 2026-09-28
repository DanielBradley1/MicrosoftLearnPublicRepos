<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Manage SharePoint Embedded containers for Copilot Notebooks, Copilot Pages, or Loop workspaces

## At a glance

| Task | Tool | Command/Location |
| --- | --- | --- |
| **View containers** | SharePoint admin center | **SharePoint Embedded** > **Active containers** |
| **List user-owned containers** | PowerShell | `Get-SPOContainer -OwningApplicationId '<AppID>' \| WHERE OwnershipType -EQ 'UserOwned'` |
| **Find ownerless workspaces** | PowerShell | `Get-SPOContainer -OwningApplicationId '<AppID>' \| WHERE {$_.OwnersCount -eq 0}` |
| **Manage membership and grant access** | SharePoint admin center | Add, remove, or change roles for Owners and Editors \(Manager in admin center\).  <br>Copy the Container Redirect URL to send to new members. See [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide). |

IT admins can manage SharePoint Embedded containers like they manage SharePoint sites using either [SharePoint Admin Center](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/consuming-tenant-admin/ctaux) or [PowerShell](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/consuming-tenant-admin/ctapowershell), with the appropriate [SharePoint Embedded administrator role](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/adminrole). Install the [latest version of SharePoint PowerShell module](https://learn.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online). Storage and quota are combined with SharePoint in your organization. Use the Loop owning application ID to filter to Loop containers in PowerShell:

- Loop owning application ID: `a187e399-0c36-4b98-8f04-1edc167a0996`
- Copilot Pages and Copilot Notebooks use the same user-owned container as Loop My workspace. In admin tools, that container is identified using the Loop owning application ID.

Note

`Get-SPOContainer` returns lists of containers in pages, so don't assume that the first response includes every matching container. To retrieve additional pages, use `-Paged` to receive a paging token, and then use `-Paged -PagingToken '<PagingToken>'` to retrieve the next page. Apply any `WHERE` filter to each page. For the latest paging behavior, limits, and syntax, see [Get-SPOContainer](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/get-spocontainer).

## Ownerless workspaces

IT admins can use SharePoint Admin Center and PowerShell to find ownerless tenant-owned Loop workspaces. For more information, see [Consuming Tenant Admin](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/cta), and [Get-SPOContainer](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/get-spocontainer).

To find ownerless Loop containers, update the following sample PowerShell to your needs:

```PowerShell
Get-SPOContainer -OwningApplicationId 'a187e399-0c36-4b98-8f04-1edc167a0996' | WHERE {$_.OwnersCount -eq 0} | FT
```

To assign new owners to an ownerless workspace and send them the Container Redirect URL, see [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide).

## Roles and membership

The SharePoint admin center uses different role names than the Loop app. Use the following mapping when managing membership:

| SharePoint admin center role | Loop app role | Description |
| --- | --- | --- |
| **Owner** | Owner | Full control, including managing membership |
| **Manager** | Editor | Can edit content but can't manage membership |
| **Writer** | Not used | Don't assign this role. The Loop app doesn't use it. |
| **Reader** | Not used | Don't assign this role. The Loop app doesn't use it. |

Important

Only assign the Owner and Editor \(Manager in admin center\) roles. The Writer and Reader roles aren't used by the Loop app and shouldn't be assigned to container members.

### Tenant-owned workspaces

Tenant-owned Loop workspaces created on or after April 2025: Manage Owners and Editors \(Manager in admin center\) directly in the admin center.

Tenant-owned Loop workspaces created before April 2025: A legacy roster still controls membership. The legacy roster is being deprecated. Until fully retired:

- Owners and Editors \(Manager in admin center\) can manage membership in the Loop app.
- SharePoint admin center changes apply only to workspaces created on or after April 2025.

### Granting access and sending the Container Redirect URL

When you add a new Owner or Editor \(Manager in admin center\), or promote an existing Editor to Owner, the new member might need a link to access the container in the Loop app. Copy the **Container Redirect URL** from the **General** tab of the container details panel and send it to the member. For the full workflow, including scenarios like user departure and ownerless workspaces, see [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide).

## Listing all the user-owned containers

To get a list of all user-owned containers in your organization, regardless of the container name, update the following sample PowerShell to your needs. This list includes the personal user-owned containers shared by Copilot Pages, Copilot Notebooks, and Loop My workspace — all returned under the Loop owning application ID, even if a given container only stores Copilot Pages or Copilot Notebooks:

```PowerShell
Get-SPOContainer -OwningApplicationId 'a187e399-0c36-4b98-8f04-1edc167a0996' | WHERE OwnershipType -EQ 'UserOwned' | FT
```

## Migrations

Currently, there's no supported method to transfer an existing SharePoint Embedded container between Microsoft 365 tenants, for example, in scenarios involving mergers or acquisitions. Within a Multi-Geo tenant, you can [move eligible SharePoint Embedded container sites to another geography](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-spo?view=o365-worldwide#move-a-sharepoint-site-or-sharepoint-embedded-container-site).

## Related articles

### Copilot Pages and Copilot Notebooks

- [Summary of compliance, lifecycle, governance](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-compliance-summary?view=o365-worldwide)
- [Requirements](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-requirements?view=o365-worldwide)
- [Storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide)
- [Permissions](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-permission?view=o365-worldwide)
- [Admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide)
- [Purview management](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide)

### Loop

- [Summary of compliance, lifecycle, governance](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-compliance-summary?view=o365-worldwide)
- [Requirements](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-requirements?view=o365-worldwide)
- [Storage](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide)
- [Permissions](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-permission?view=o365-worldwide)
- [Admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide)
- [UX examples for admin policy states](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-ux-examples?view=o365-worldwide)
- [Overview of Loop components in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-components-teams?view=o365-worldwide)
- [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide)
