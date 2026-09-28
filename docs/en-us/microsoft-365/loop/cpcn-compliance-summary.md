<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-compliance-summary?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Summary of governance, lifecycle, and compliance capabilities for Copilot Pages and Copilot Notebooks

As a Compliance Manager or IT administrator, it's crucial to stay up-to-date on the latest governance, data lifecycle, and compliance posture for the software solutions being used in your organization. This article details the capabilities available and not available yet for Copilot Pages and Copilot Notebooks.

## At a glance

| Capability | Status |
| --- | --- |
| **Admin policy** | ✅ Available - [Cloud Policy](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide) |
| **GDPR / EUDB** | ✅ Supported |
| **Conditional Access** | ◐ App-level only \(entire Microsoft Copilot app\) |
| **Information Barriers** | ❌ Not supported |
| **Customer Lockbox** | ✅ Supported |
| **eDiscovery** | ✅ Supported |
| **Legal Hold** | ✅ Supported; selecting the container in the custodian data source picker is rolling out \(expected October 2026\) |
| **Retention policies** | ✅ Supported via "All SharePoint Sites" |
| **Retention labels** | ◐ Limited manual application |
| **Sensitivity labels** | ✅ Copilot Pages only |
| **DLP** | ✅ Supported with policy tips |
| **Recycle bin** | ❌ No end-user recycle bin for Copilot Notebooks |

## SharePoint Embedded

Copilot Pages and Copilot Notebooks content are stored in SharePoint Embedded. Content stored in SharePoint Embedded containers follows the [SharePoint Embedded security and compliance documentation](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/compliance/security-and-compliance). The sections below outline governance, lifecycle, and compliance capabilities applicable to all Copilot Pages and Copilot Notebooks storage types.

## Foundations

- **Admin policy**: Use [Cloud Policy](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide) to turn on or off creation of Copilot Pages and Copilot Notebooks. Copilot Pages can also be shared as Loop components in supporting apps. See [relationship to Loop components](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide#relationship-to-loop-components).
- **GDPR**: Data subject requests can be serviced through the [Microsoft Purview portal](https://learn.microsoft.com/en-us/compliance/regulatory/gdpr-data-subject-requests#data-subject-request-admin-tools) and [Purview eDiscovery workflows](https://learn.microsoft.com/en-us/purview/ediscovery).
- **EUDB**: Compliance is supported. See [What is the EU Data Boundary?](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn)

## Data security and devices

- **Intune**: [Device Management Support](https://learn.microsoft.com/en-us/intune/device-management/actions) is available for the Microsoft 365 app and Teams app on iOS and Android.
- **Conditional Access**: Only applies at the app level. Because Copilot Pages and Copilot Notebooks are features of the Microsoft Copilot app, [Conditional Access](https://learn.microsoft.com/en-us/sharepoint/control-access-from-unmanaged-devices) applies to the entire app at m365.cloud.microsoft. Use [admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide) to block creation of new content.
- **Information Barriers**: [Not supported](https://learn.microsoft.com/en-us/purview/information-barriers-sharepoint). See [admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide) for available controls.

Important

Information Barriers are **not supported** for content stored in SharePoint Embedded containers. Copilot Pages and Copilot Notebooks use SharePoint Embedded for storage. If your organization requires Information Barriers, consider using [admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide) to disable Copilot Pages and Copilot Notebooks.

- **Customer Lockbox**: [Supported](https://learn.microsoft.com/en-us/purview/customer-lockbox-requests).
- **Guest app access**: Available for Copilot Pages and Copilot Notebooks containers. Enables third-party export/eDiscovery tools, migration tools, and developer APIs. Use PowerShell to [Get](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/get-spoapplication) and [Set](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spoapplicationpermission) guest app permissions.

## Data lifecycle

- **Scenario: user leaves the organization.** The container follows the same [OneDrive deletion lifecycle](https://learn.microsoft.com/en-us/sharepoint/retention-and-deletion#the-onedrive-deletion-process) as the rest of Microsoft 365, with one manual handoff step at departure \(access and notification aren't automatic\) and the option to permanently reassign the container to a new owner. For the full process, options, and comparison with OneDrive, see [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide#options-when-a-user-leaves-the-organization). To preserve content before departure, export it using Purview or the Graph API, or add the container to a retention policy.
- **Storage**: Copilot Pages and Copilot Notebooks are stored together in a single user-owned SharePoint Embedded container, which is also shared by Loop My workspace. Storage counts against your organization's SharePoint quota. See [storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide) for the full explanation of the shared container and [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide) for admin tooling.

  - **Limitation**: There's no admin control to set quota limits on individual containers.
  - **Admin control note**: To prevent the container from being created, disable both the Copilot Pages and Copilot Notebooks policy and the Loop **Create Loop workspaces in Loop** policy for the same user.

- **Multi-Geo**: [Supported](https://learn.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-multi-geo). The container is created in the geo matching the user's [preferred data location](https://learn.microsoft.com/en-us/microsoft-365/enterprise/plan-for-multi-geo#best-practices).

  - **Known issue**: Some operations might not work correctly after moving containers across geos. Microsoft is working on a fix.

- **Recycle bin**: No end-user recycle bin exists.

  - **Limitation**: Neither administrators nor end users can recover individually deleted Copilot Notebooks.

- **Version History**: [Export in Purview](https://learn.microsoft.com/en-us/purview/ediscovery-export-search-results#step-1-prepare-search-results-for-export) or via [Graph API](https://learn.microsoft.com/en-us/graph/api/driveitem-get-content-format). 50 major versions per file by default, configurable [via PowerShell](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spoapplication#-itemmajorversionlimit) per application.
- **Audit logs**: Available for all events. Retained, exportable, and streamable to third-party tools. Search in [Purview](https://purview.microsoft.com/auditlogsearch) for "page" and filter by `"SourceFileExtension":"page"`. Copilot Notebooks create and update `.pod` files to manage content.

## eDiscovery

- **Purview eDiscovery**: [Supported](https://learn.microsoft.com/en-us/purview/ediscovery-premium-get-started) for search/collection, review \(Premium license required\), and export as HTML \(Premium license required\) or original format. Download and reupload files to OneDrive to view in native format.
- **Graph API export**: [Supported](https://learn.microsoft.com/en-us/graph/api/driveitem-get-content-format) for third-party tools. Use PowerShell to [Get](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/get-spoapplication) and [Set](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spoapplicationpermission) guest application permissions.
- **Legal Hold**: Supported. Content is stored in the [Preservation Hold Library](https://learn.microsoft.com/en-us/sharepoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server).

  - When you add a user as a [custodian](https://learn.microsoft.com/en-us/purview/ediscovery-add-custodians-to-case) in Purview eDiscovery, selecting their user-owned SharePoint Embedded container as a data source in the same experience where you select the user's OneDrive and Exchange mailbox is rolling out and expected in October 2026.
  - Until then, retrieve the user-owned container URL using PowerShell or the SharePoint admin center, then add it as a data source manually. For instructions, see [Retrieving the container URL for Purview](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide#retrieving-the-container-url-for-purview).

## Microsoft 365 retention and deletion

- **[Retention policies](https://learn.microsoft.com/en-us/purview/create-retention-policies?tabs=other-retention)** from Microsoft Purview Data Lifecycle Management configured for all SharePoint sites are enforced for all Copilot Pages and Copilot Notebooks.

  - For more information on how to configure specific Copilot Notebooks, see [Purview and SharePoint Embedded](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide).

- **[Retention labels](https://learn.microsoft.com/en-us/purview/retention#retention-labels)** from Microsoft Purview Data Lifecycle Management and Microsoft Purview Records Management are supported for Copilot Pages \(.page files\) and Copilot Pages in Copilot Notebooks by [applying published labels](https://learn.microsoft.com/en-us/purview/create-apply-retention-labels?tabs=spo-onedrive) in OneDrive or SharePoint, or [automatically applying](https://learn.microsoft.com/en-us/purview/apply-retention-labels-automatically) the labels. There's limited support for manually applying retention labels.

  - Retention labels can't be viewed or applied directly from a Copilot Page. Instead, the user must [navigate to the Copilot Page within the Loop app](https://learn.microsoft.com/en-us/purview/create-apply-retention-labels?tabs=loop%2Cdefault-label-for-sharepoint#manually-apply-retention-labels) to view or apply a retention label on a Copilot Page.
  - Retention labels that mark the content as a record or regulatory record can't be manually applied in either the Copilot Page or when the content is opened in the Loop app. If content is automatically labeled as a record, locking and unlocking this record is not yet available.

## Information protection

- **Sensitivity labels**: [Available](https://learn.microsoft.com/en-us/purview/sensitivity-labels-loop) for Copilot Pages. Copilot Notebooks don't have container sensitivity labels because they share a container with all Copilot Pages.
- **Data Loss Prevention \(DLP\)**: [Rules enforced](https://learn.microsoft.com/en-us/purview/dlp-learn-about-dlp) with end-user policy tip support.

## Related articles

- [Requirements](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-requirements?view=o365-worldwide)
- [Storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide)
- [Permissions](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-permission?view=o365-worldwide)
- [Admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide)
- [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
- [Purview management](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide)
- [Grant access to containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide)
