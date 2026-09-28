<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-permission?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# Overview of Copilot Pages and Copilot Notebooks permissions

## Content permissions mechanism

Copilot Pages and Copilot Notebooks are stored in user-owned [SharePoint Embedded](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/admin-exp/consuming-tenant-admin/cta) containers. In the SharePoint admin center and PowerShell, these containers have an **application name of `Loop`** because the user-owned container is shared with Loop My workspace.

### Sharing Mechanism

- **Copilot Notebooks** can be shared. For end-user instructions, see [How to Share a Microsoft Copilot Notebook](https://support.microsoft.com/en-us/topic/how-to-share-a-microsoft-365-copilot-notebook-e8faaac5-4976-402d-b0a3-ea61f01555ff).

  - Chat conversations in shared Copilot Notebooks are private and each user has their own set of chats.
  - Anyone you share with gains access to all the files referenced in the notebook.
  - Access to linked files is granted automatically where possible. Some linked files might remain restricted if permissions can't be updated.
  - If your notebook includes a Microsoft OneNote section or page, you'll need to share the entire OneNote notebook so others can access that content. [Learn more about how to share a OneNote notebook.](https://support.microsoft.com/en-us/office/how-to-share-a-onenote-notebook-d4a74a14-44a3-411e-8fb5-06e73ddf047f)

- **Page Sharing**: Grants access to a specific page \(not the whole notebook\) with options for edit or read-only access. The user can choose to use a company share link or people-specific share link, based on your organizational sharing settings.

  ![Screenshot showing the Share button in the upper corner of a Copilot Page.](https://learn.microsoft.com/en-us/microsoft-365/loop/media/cpcn-share-page.png?view=o365-worldwide) The Share button in the upper corner of a Copilot Page.

  ![Screenshot showing the Sharing Link copied to clipboard dialog with Settings option.](https://learn.microsoft.com/en-us/microsoft-365/loop/media/cpcn-share-link.png?view=o365-worldwide) After choosing Page or Component in the Share button \(previous screen\), The share link is copied to the clipboard, and sharing Settings are available.

  ![Screenshot showing the Share settings available for the Copilot Page permissions.](https://learn.microsoft.com/en-us/microsoft-365/loop/media/cpcn-share-settings.png?view=o365-worldwide) The share link settings and permissions configuration, just like all other files in SharePoint or OneDrive.

## Guest/External sharing

External users \(guests\) can't access shared Copilot Pages directly via link. Copilot Notebooks don't support external sharing.

**Workaround for external access:** If an external user manually adds a Copilot Page sharing link to their Loop workspace and cross-tenant guest access is configured, they can access the page within the Loop workspace experience.

### Disabling guest sharing

To disable guest sharing for Copilot Pages and Copilot Notebooks containers, see [application external sharing override](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/sharing-and-perm#application-external-sharing-override) and use application ID `a187e399-0c36-4b98-8f04-1edc167a0996`. This setting controls external sharing for all SharePoint Embedded containers of this type.

## Related articles

- [Summary of compliance, lifecycle, governance](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-compliance-summary?view=o365-worldwide)
- [Requirements](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-requirements?view=o365-worldwide)
- [Storage](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-storage?view=o365-worldwide)
- [Admin policies](https://learn.microsoft.com/en-us/microsoft-365/loop/cpcn-admin-configuration?view=o365-worldwide)
- [Managing SharePoint Embedded containers](https://learn.microsoft.com/en-us/microsoft-365/loop/spe-management?view=o365-worldwide)
- [Purview management](https://learn.microsoft.com/en-us/microsoft-365/loop/purview-management?view=o365-worldwide)
