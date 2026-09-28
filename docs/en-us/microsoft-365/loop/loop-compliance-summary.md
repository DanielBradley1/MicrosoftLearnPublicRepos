<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/loop-compliance-summary?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Summary of governance, lifecycle, and compliance capabilities for Loop

This article covers compliance for Loop. For Copilot Pages and Copilot Notebooks, see the [dedicated compliance summary](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-compliance-summary?view=o365-worldwide).

As a Compliance Manager or IT administrator, it's crucial to stay up-to-date on the latest governance, data lifecycle, and compliance posture for the software solutions being used in your organization. This article details the capabilities available and not available yet for [Microsoft Loop](https://www.microsoft.com/microsoft-loop).

## At a glance

| Capability | Status |
| --- | --- |
| **Admin policies** | ✅ Available - [Cloud Policy + SharePoint PowerShell](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide) |
| **GDPR / EUDB** | ✅ Supported |
| **Conditional Access** | ✅ Supported |
| **Information Barriers** | ◐ OneDrive/SharePoint only \(not SharePoint Embedded\) |
| **Customer Lockbox** | ✅ Supported |
| **eDiscovery** | ✅ Supported |
| **Legal Hold** | ✅ Supported; selecting the My workspace container in the custodian data source picker is rolling out \(expected October 2026\) |
| **Retention policies** | ✅ Supported |
| **Retention labels** | ◐ Limited manual application |
| **Sensitivity labels** | ✅ Pages, components, and workspaces |
| **DLP** | ✅ Supported with policy tips |
| **Recycle bin** | ✅ Components and pages; ❌ Workspaces |

## SharePoint Embedded

Loop content storage varies based on creation method. For detailed information about storage locations, see [storage](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide). Content stored in SharePoint Embedded containers follows the [SharePoint Embedded security and compliance documentation](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/compliance/security-and-compliance).

The sections below outline governance, lifecycle, and compliance capabilities applicable to all Loop storage types. Where capabilities vary by storage location-OneDrive, SharePoint sites, or SharePoint Embedded containers-specific details are provided.

## Foundations

- **Admin policies**: Use [Cloud Policy and SharePoint PowerShell](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide) to control creation of Loop components, pages, and workspaces. When creation is disabled, existing content renders as hyperlinks instead of interactive components.

  - Primary policy controls most apps \(excluding Teams\); secondary policies control Outlook, Teams, and collaborative meeting notes separately.

- **GDPR**: Data subject requests can be serviced through the [Microsoft Purview portal](https://learn.microsoft.com/en-us/compliance/regulatory/gdpr-data-subject-requests#data-subject-request-admin-tools) and [Purview eDiscovery workflows](https://learn.microsoft.com/en-us/purview/ediscovery).
- **EUDB**: Compliance is supported. See [What is the EU Data Boundary?](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn)

## Data security and devices

- **Intune** [Device Management Support](https://learn.microsoft.com/en-us/intune/device-management/actions) exists for Microsoft 365 app, Teams app, and Loop app, on iOS and Android.
- **[Conditional Access](https://learn.microsoft.com/en-us/sharepoint/control-access-from-unmanaged-devices)** is supported.
- **[Information Barriers](https://learn.microsoft.com/en-us/purview/information-barriers-sharepoint)** are enforced for content stored in SharePoint sites or OneDrive.

Important

Information Barriers are **not supported** for content stored in SharePoint Embedded containers \(Loop workspaces and My workspace\). If your organization requires Information Barriers, consider using [admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide) to restrict Loop workspace creation.

- **Customer Lockbox**: [Supported](https://learn.microsoft.com/en-us/purview/customer-lockbox-requests).
- **Guest app access**: Available for Loop workspace containers. Enables third-party export/eDiscovery tools, migration tools, and developer APIs. Use PowerShell to [Get](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/get-spoapplication) and [Set](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spoapplicationpermission) guest app permissions.

## Data lifecycle

- Loop's My workspace shares a single user-owned SharePoint Embedded container with Copilot Pages and Copilot Notebooks; this container has an **application name of `Loop`** in admin tools. Shared Loop workspaces create one SharePoint Embedded container per workspace. These containers don't have individual storage limits; instead, their storage usage counts toward your organization's overall SharePoint storage quota. There's no admin control to set storage limits for individual SharePoint Embedded containers. Loop files in their OneDrive and SharePoint locations follow the quotas of those storage locations. For the full explanation of the shared user-owned container \(naming, creation rules, lifecycle\), see [storage](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide).
- See [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide) for information and workflows within SharePoint admin center or PowerShell.

  Note

  The Loop My workspace follows the same [OneDrive deletion lifecycle](https://learn.microsoft.com/en-us/sharepoint/retention-and-deletion#the-onedrive-deletion-process), with one manual handoff step at departure \(access and notification aren't automatic\) and the option to permanently reassign the container to a new owner. For the full process, options, and comparison with OneDrive, see [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide#options-when-a-user-leaves-the-organization).
- **[Multi-Geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo)**: Supported for My workspace and shared Loop workspaces. Content is created in the geo matching the user's or group's [preferred data location](https://learn.microsoft.com/en-us/microsoft-365/enterprise/plan-for-multi-geo#best-practices). Loop content in OneDrive and SharePoint follows the multi-geo capabilities of those services.

  - To move a workspace to a different geo, use the [same mechanism as SharePoint Communication sites](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-service-spo?view=o365-worldwide#move-a-sharepoint-site-or-sharepoint-embedded-container-site).


  Important


  Some operations in Loop workspaces \(such as sharing or creating new pages\) might not function correctly immediately after moving containers across geos. Microsoft is working on a fix.

- End-user **Recycle bin** for deleted Loop components and pages is available within the Loop workspace, OneDrive, or SharePoint site.

  Important

  There's no end user recycle bin for Loop workspaces. Furthermore, restoring the Loop workspace using admin tooling doesn't update in the Loop app user experience. The user would need to visit a saved page link for a restored workspace in order to see it again.
- **Version History** [Export in Purview](https://learn.microsoft.com/en-us/purview/ediscovery-export-search-results#step-1-prepare-search-results-for-export) or via [Graph API](https://learn.microsoft.com/en-us/graph/api/driveitem-get-content-format) is available. Loop workspace content stored in SharePoint Embedded \(See [storage](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide) for more information\), version history is configured to save 50 major versions per file by default, configurable [via PowerShell](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spoapplication#-itemmajorversionlimit) per application. Loop files in OneDrive or SharePoint follow the same file versioning settings as other files.
- **Audit** logs exist for all events. They're retained, can be exported, and can be streamed to third party tools. For more information, see [Purview](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide#searching-the-audit-logs).

## eDiscovery

- **Purview eDiscovery**: [Supported](https://learn.microsoft.com/en-us/purview/ediscovery-premium-get-started) for search/collection, review \(Premium license required\), and export as HTML \(Premium license required\) or original format. Download and reupload files to OneDrive to view in native format.
- **Graph API export**: [Supported](https://learn.microsoft.com/en-us/graph/api/driveitem-get-content-format) for third-party tools. Use PowerShell to [Get](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/get-spoapplication) and [Set](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spoapplicationpermission) guest application permissions.
- **Legal Hold**: Supported. Content is stored in the [Preservation Hold Library](https://learn.microsoft.com/en-us/sharepoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server).

  - When you add a user as a [custodian](https://learn.microsoft.com/en-us/purview/ediscovery-add-custodians-to-case) in Purview eDiscovery, selecting their user-owned SharePoint Embedded container \(Loop My workspace\) as a data source in the same experience where you select the user's OneDrive and Exchange mailbox is rolling out and expected in October 2026.
  - Until then, retrieve the user-owned container URL using PowerShell or the SharePoint admin center, then add it as a data source manually. For instructions, see [Retrieving the container URL for Purview](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide#retrieving-the-container-url-for-purview).

## Microsoft 365 retention and deletion

- **[Retention policies](https://learn.microsoft.com/en-us/purview/create-retention-policies?tabs=other-retention)** from Microsoft Purview Data Lifecycle Management configured for all SharePoint sites are enforced for all .loop files or alternatively can be [configured per Loop workspace](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide#retrieving-the-container-url-for-purview).

  - For more information on how to configure specific Loop workspaces, see [Purview and SharePoint Embedded](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide).

- **[Retention labels](https://learn.microsoft.com/en-us/purview/retention#retention-labels)** from Microsoft Purview Data Lifecycle Management and Microsoft Purview Records Management are supported for Loop components by [applying published labels](https://learn.microsoft.com/en-us/purview/create-apply-retention-labels?tabs=spo-onedrive) in OneDrive or SharePoint, or [automatically applying](https://learn.microsoft.com/en-us/purview/apply-retention-labels-automatically) the labels. There's limited support for manually applying retention labels.

  - Retention labels can't be viewed or applied directly from a Loop component. Instead, the user must [navigate to the Loop file within the Loop app](https://learn.microsoft.com/en-us/purview/create-apply-retention-labels?tabs=loop%2Cdefault-label-for-sharepoint#manually-apply-retention-labels) to view or apply a retention label on a Loop component.
  - Retention labels that mark the content as a record or regulatory record can't be manually applied in either the Loop component or when the content is opened in the Loop app. If content is automatically labeled as a record, locking and unlocking this record isn't yet available.
  - For clarification only, not a limitation: retention labels don't apply to containers like SharePoint sites or Loop workspaces; instead, use retention policies for these containers. To learn more, see [retention](https://learn.microsoft.com/en-us/purview/retention).

## Information protection

- **Sensitivity labels**: [Available](https://learn.microsoft.com/en-us/purview/sensitivity-labels-loop) for Loop pages and components. Workspace sensitivity labels are configurable per workspace \(at container level\) via SharePoint Admin Center and PowerShell. See [configuring sensitivity labels](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/security-and-compliance#security-features).

  - **Note**: There's no admin setting to configure guest sharing of specific Loop workspaces. Use container sensitivity labeling for per-workspace external sharing configuration.

- **Data Loss Prevention \(DLP\)**: [Rules enforced](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp) with end-user policy tip support.

## Related articles

- [Requirements](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-requirements?view=o365-worldwide)
- [Storage](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-storage?view=o365-worldwide)
- [Permissions](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-permission?view=o365-worldwide)
- [Admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-admin-configuration?view=o365-worldwide)
- [UX examples for admin policy states](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-ux-examples?view=o365-worldwide)
- [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
- [Purview management](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide)
- [Overview of Loop components in Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/loop/loop-components-teams?view=o365-worldwide)
- [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide)
