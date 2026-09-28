<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Purview management for SharePoint Embedded containers

This article covers Purview integration for SharePoint Embedded containers used by Copilot Pages, Copilot Notebooks, and Loop workspaces. The concepts apply to all these products because they share the same underlying SharePoint Embedded infrastructure.

For personal user-owned containers, Copilot Pages, Copilot Notebooks, and Loop My workspace use the same physical SharePoint Embedded container. In admin tools and audit data, that container is identified as owned by Loop.

## At a glance

| Task | How to do it |
| --- | --- |
| **Apply retention to all containers** | Use "All SharePoint Sites" scope in Purview |
| **Apply retention to specific container** | Get container URL from SharePoint admin center, add to Purview policy |
| **Search audit logs** | Search for "page", "loop", or the Loop Application IDs |
| **Filter audit exports** | Use `"SourceFileExtension":"page"` or `"SourceFileExtension":"loop"` |

All SharePoint Embedded containers are targeted using the "All SharePoint Sites" scope in Microsoft Purview. For example, if configuring Retention Policies, the configuration you specify that targets All SharePoint Sites applies to every Copilot Pages and Copilot Notebooks container in SharePoint Embedded, and every Loop workspace in SharePoint Embedded. All SharePoint Sites includes all SharePoint Embedded container ownership types: user, group, and tenant-owned.

## Retrieving the container URL for Purview

Purview enables configuration of retention policies and other compliance features based on the content URL location. To locate the container URL for Copilot Pages, Notebooks, or Loop workspaces:

1. Sign in to the SharePoint admin center with the [SharePoint Embedded administrator role](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/adminrole)
2. Expand **SharePoint Embedded**, and then select **Active containers** or **Deleted containers**, where you can view the details of a selected Loop workspace or Copilot Pages and Copilot Notebooks container.
3. From the flyout pane, **General** tab.
4. Copy the container URL.

The container URL doesn't provide access to the container and doesn't function as a shareable link. Use it only within Purview to target the container for Purview features. To give end users a clickable link that opens the container in the Loop app, use the separate **Container Redirect URL** instead. For more information, see [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide).

## Searching the Audit Logs

Loop application IDs:

- Loop Web Application ID: `a187e399-0c36-4b98-8f04-1edc167a0996`
- Loop Mobile Application ID: `0922ef46-e1b9-4f7e-9134-9ad00547eb41`
- The personal user-owned container shared by Copilot Pages, Copilot Notebooks, and Loop My workspace is identified using the Loop Application IDs.

Because these workloads share an application identity, audit events for Copilot Pages and Copilot Notebooks also appear under the Loop application IDs — there's no separate Copilot Pages or Copilot Notebooks identity to filter on in audit logs or eDiscovery.

### Search and Export

To search and export Microsoft 365 service events for all file related activity:

1. In the [Purview audit logs search](https://purview.microsoft.com/auditlogsearch), search audit logs for "page" or "loop" or "loot" or "fluid" or for the Loop Application IDs in the **Keyword Search** filter
2. Further filter exported results by "SourceFileExtension":"page" or "SourceFileExtension":"loop" or "SourceFileExtension":"loot" \(templates\) or "SourceFileExtension":"fluid" \(deprecated\)

   Loop workspaces create and update `.pod` files to manage content in the workspace.

### Specific Loop workspace or Copilot Notebook

To search for audit events related to a specific Loop workspace or a Copilot Pages and Copilot Notebooks container, follow these steps:

1. [Retrieve the container URL](#retrieving-the-container-url-for-purview) for the Loop workspace or Copilot Notebook you want to audit.
2. In the [Purview audit logs search](https://purview.microsoft.com/auditlogsearch), use the following filters:

   - **File, folder, or site**: Enter the full container URL and append `/*` to include all file and container audit events.

     - Example: `https://<your-tenant>.sharepoint.com/contentstorage/CSP_c33f9fa3-9cbe-4fac-ba1f-b8eeb9c30e23/*`

   - **Keyword Search**: To find all audit events related to the container, extract the GUID from the container URL and enter it in the Keyword Search filter.

     - In the preceding example, the GUID is `c33f9fa3-9cbe-4fac-ba1f-b8eeb9c30e23`.


   This approach ensures you capture all relevant audit events for the selected Loop workspace or the Copilot Pages and Copilot Notebooks container.

## Related articles

- [Summary of compliance, lifecycle, governance - Copilot Pages and Copilot Notebooks](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-compliance-summary?view=o365-worldwide)
- [Summary of compliance, lifecycle, governance - Loop](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-compliance-summary?view=o365-worldwide)
- [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
- [Copilot Pages and Notebooks storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide)
- [Loop storage](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide)
