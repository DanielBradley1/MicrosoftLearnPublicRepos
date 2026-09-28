<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/copilot-pages-ediscovery?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Use eDiscovery with Copilot Pages

Copilot Pages are collaborative canvases where users and Microsoft Copilot can create and refine content together in real time. A Copilot Page is a shareable `.page` file. Microsoft Purview eDiscovery supports preserving, searching, reviewing, and exporting this content.

Use this article to understand how Copilot Pages are stored and shared, identify the correct data source, and work with the content that you collect. For information about using Copilot Pages, see [Get started with Microsoft Copilot Pages](https://support.microsoft.com/topic/6674bd51-9ff5-42c4-9256-44d9428a726f).

## Before you begin

- Make sure that you have the required [eDiscovery permissions](https://learn.microsoft.com/en-us/purview/edisc-permissions).
- Review the [licensing requirements for eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-get-started#subscriptions-and-billing).
- Create or open an [eDiscovery case](https://learn.microsoft.com/en-us/purview/ediscovery-create-and-manage-cases).

Reviewers require the appropriate Microsoft Purview license to review or export content as HTML. For details, see [Get started with eDiscovery](https://learn.microsoft.com/en-us/purview/ediscovery-premium-get-started).

## Understand Copilot Pages in eDiscovery

From an eDiscovery perspective, a Copilot Page is:

- A file stored in SharePoint, OneDrive, or SharePoint Embedded, similar to how a Word document is stored.
- A collaborative document, not a form of electronic communication such as an email or Teams message.
- A file that users share as a link or cloud attachment. Sharing doesn't create a separate copy of the file.

Copilot Pages use the same underlying technology as Loop components. This technology enables real-time coauthoring by users and Copilot while keeping content synchronized for collaborators.

## Understand the storage location

Pages stored in SharePoint or OneDrive are managed by the owner of the storage location or by an administrator. Pages stored in SharePoint Embedded containers are managed by the owning application.

Each user has one user-owned SharePoint Embedded container for their Copilot Pages, Copilot Notebooks, and Loop My workspace content. In the SharePoint admin center and Microsoft Purview, the container has the application name `Loop`. It doesn't have a separate Copilot Pages or Copilot Notebooks application identity. The container might be named **Pages** or **My workspace**, depending on which experience created it first.

SharePoint Embedded is an API-only file and document management system. Unlike a classic SharePoint site, a SharePoint Embedded container doesn't have a standalone user interface or a user-assigned URL path.

| Feature | Classic SharePoint site | SharePoint Embedded container |
| --- | --- | --- |
| **Access** | SharePoint browsing experience | Owning application or Microsoft Graph APIs |
| **URL structure** | `.../sites/<SiteName>/` | `.../contentstorage/CSP_<GUID>` |
| **Naming** | User or administrator assigns the site name and URL | Display name is stored in metadata; URL contains a GUID |
| **Ownership** | Tenant-owned; site owners managed through SharePoint administration | User-owned, tenant-owned, or group-owned |
| **Typical use** | Intranets, team sites, and collaboration | Application file storage, such as Copilot Pages, Copilot Notebooks, and Loop workspaces |

For more information, see [Overview of Copilot Pages and Copilot Notebooks storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide) and [SharePoint Embedded overview](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/overview).

## Understand shared Copilot Pages

When a user shares a Copilot Page, Microsoft 365 shares a link to the underlying `.page` file:

- In a Teams message, Teams displays a preview of the linked file.
- In an Outlook email, Outlook displays the cloud attachment link in the message body as a preview.
- In other supported Microsoft 365 apps, the app references the Page by its URL.

The message or email and the linked Copilot Page are separate eDiscovery items. Collect the storage location that contains the `.page` file when the Page itself is in scope.

## Understand version history

Copilot Pages use file-level version history. Versioning generally works as follows:

- The initial file upload creates the first version, which is typically empty.
- A new version might be created when more than five minutes have passed since the previous version or when the editing session closes.
- As with other coauthored Microsoft 365 documents, the service might aggregate changes from multiple users into one version. One user is listed as the modifier, and audit records identify the other authors.
- System operations don't replace the current user as the modifier.
- Pages stored in OneDrive or SharePoint have a default limit of 512 versions, which administrators can configure.
- Pages stored in SharePoint Embedded have a default limit of 50 major versions. Administrators can configure this limit for the application by using the [`Set-SPOApplication`](https://learn.microsoft.com/en-us/powershell/module/microsoft.online.sharepoint.powershell/set-spoapplication#-itemmajorversionlimit) cmdlet.

When a Page is subject to an eDiscovery hold, the configured version limit is ignored and all versions are retained. Versions might accumulate beyond the configured limit until the hold is released. Normal version-limit enforcement resumes after the hold is released.

Note

When a user shares a Copilot Page link in an email or Teams message, eDiscovery might retrieve the version closest to the communication's timestamp, as it does for other documents shared as links or cloud attachments.

For more information, see [Version history limits for document libraries and OneDrive](https://learn.microsoft.com/en-us/sharepoint/document-library-version-history-limits).

Important

Selecting a user's OneDrive as a data source doesn't include their Copilot Pages or Copilot Notebooks. Include the user's SharePoint Embedded container as a separate data source.

## Locate the user's container

1. Sign in to the [SharePoint admin center](https://go.microsoft.com/fwlink/?linkid=2185219) with the [SharePoint Embedded administrator role](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/adminrole).
2. Expand **SharePoint Embedded**, and then select **Active containers**.
3. Filter the list by **Application name: Loop** and **Ownership type: User**.
4. Search for the user in the **Principal owner** field.
5. Select the container, and then copy its container URL from the **General** tab.

The container URL identifies the location for Microsoft Purview. It doesn't grant access and isn't a link that users can open. For more information about container URLs, see [Retrieve the container URL for Purview](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide#retrieving-the-container-url-for-purview).

## Add the container to an eDiscovery case

1. In the [Microsoft Purview portal](https://purview.microsoft.com), open **eDiscovery**, and then open your case.
2. Add the user as a [custodian](https://learn.microsoft.com/en-us/purview/ediscovery-add-custodians-to-case).
3. Select the user's SharePoint Embedded container as a data source. If the container isn't available in the custodian data source picker, add the container URL as a site data source.
4. Apply a hold if the case requires content preservation. For instructions, see [Create an eDiscovery hold](https://learn.microsoft.com/en-us/purview/ediscovery-create-holds).

Legal holds are supported for Copilot Pages and Copilot Notebooks. Held content is retained in the [Preservation Hold Library](https://learn.microsoft.com/en-us/sharepoint/governance/ediscovery-and-in-place-holds-in-sharepoint-server).

## Search and collect content

Create a search or collection that includes the SharePoint Embedded container data source. To search across all supported SharePoint and SharePoint Embedded locations instead, include all SharePoint sites in the search scope.

Use keywords, date ranges, participants, and other supported conditions to narrow the results. Copilot Pages use the `.page` file extension.

For instructions, see [Search for content in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-search-query) and [Create a review set](https://learn.microsoft.com/en-us/purview/edisc-review-set-manage).

## Review and export content

Microsoft Purview eDiscovery supports collecting and exporting Copilot Pages in their original format. With the appropriate license, reviewers can add collected content to a review set and export Pages as HTML. Microsoft Graph also supports [converting Pages to other formats](https://learn.microsoft.com/en-us/graph/api/driveitem-get-content-format).

Downloaded `.page` files don't open directly in the native Copilot Pages experience. To view a supported file in its native experience, upload it to OneDrive, and then open it from there.

For export instructions, see [Export search results in eDiscovery](https://learn.microsoft.com/en-us/purview/ediscovery-export-search-results).

## Work with sensitivity labels and encryption

Copilot Pages support Microsoft Purview sensitivity labels. Users can view or change a label by selecting the shield icon at the top of a Page, subject to their permissions and the organization's label policies.

Microsoft Purview eDiscovery supports decrypting Pages protected by supported Microsoft encryption technologies. The reviewer must have the **RMS Decrypt** role. Decryption support varies by eDiscovery tier, encryption configuration, and where encryption was applied. For requirements and limitations, see [Decryption in Microsoft Purview eDiscovery](https://learn.microsoft.com/en-us/purview/ediscovery-decryption).

## Investigate Copilot interactions

When Copilot operates on a Copilot Page, the Page is the grounding artifact for the interaction. Microsoft Purview records Copilot interactions and associates them with the Page:

- Communication Compliance records the AI prompt and response with a link to the Page where the interaction occurred.
- Prompts and responses in a Page are file edits and are subject to versioning.
- Microsoft Purview Audit \(Premium\) provides detailed Copilot activity records.
- eDiscovery can surface Copilot-generated content in Copilot Pages files.

For more information, see [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy).

## Related articles

- [Summary of governance, lifecycle, and compliance capabilities for Copilot Pages and Copilot Notebooks](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-compliance-summary?view=o365-worldwide)
- [Purview management for SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide)
- [Overview of Copilot Pages and Copilot Notebooks storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide)
- [SharePoint Embedded overview](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/overview)
- [Manage SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
- [Grant access to Copilot Pages, Copilot Notebooks, and Loop containers](https://learn.microsoft.com/en-us/microsoft-365/loop/grant-access?view=o365-worldwide)
