<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/archive/archive-compliance?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-01 -->

# Compliance features in Microsoft 365 Archive

Note

Microsoft Purview features work seamlessly with archived content. For example, you can apply retention hold on archived content without needing to unarchive it. Likewise, you can also archive content in retention hold without needing to move or delete it from retention scope.

## Data promises for archived files and sites

Just like active SharePoint content, archived sites and files maintain a baseline level of data promises, ensuring that your information is always protected and accessible:

- **Durability** - All archived data is equally as durable as active SharePoint data, meaning it remains intact and reliable over time.
- **Security** - Archived data have the same level of security as active sites and data, safeguarding your information from unauthorized access.
- **Geo residence** - All archived data stays within your geo compliance boundary, ensuring that your data residency requirements are met.
- **Microsoft EU data boundary** - All archived data complies with the EU data boundary promise, adhering to stringent data protection regulations.

## Impact on compliance offerings

Microsoft 365 Archive also affects various compliance offerings, ensuring that your archived data remains manageable and discoverable:

- **Preservation hold library \(PHL\)** - Archived files move to the Preservation Hold Library \(PHL\) when required by their retention configuration, the same as active files. Retention policies configured with the archive action continue to protect archived files and move them to the PHL when appropriate. Files that move to the PHL remain archived. Archived files in the PHL can be reactivated the same as archived files outside the PHL.
- **Data lifecycle management and records management** - Archived content still honors the retention and deletion periods from any retention policies or retention labels. For more information, see [How retention works with Microsoft 365 Archive](https://learn.microsoft.com/en-us/purview/retention-policies-sharepoint#how-retention-works-with-microsoft-365-archive).
- **eDiscovery** - eDiscovery still finds all content even if archived. eDiscovery will also be able to export directly from archived content but might take longer to export.
- **Bring your own key \(BYOK\)** - All archived content will comply with the BYOK promises, for any tenant who already uses the BYOK feature or enables it after archiving sites.
- **Permissions and access policies** - These settings and policies are retained on the site throughout the archive and reactivation lifecycle. Archiving the site and then reactivating it doesn't change the application of permissions or related access policies.
- **Audit** - Archiving, reactivation, and deletion of archived sites and files are recorded in the audit log. For more information, see [Audit log activities](https://learn.microsoft.com/en-us/purview/audit-log-activities).
- **Information protection** - Archived content still honors sensitivity label settings. Additionally, new sensitivity labels will also get applied to files in archived sites.
