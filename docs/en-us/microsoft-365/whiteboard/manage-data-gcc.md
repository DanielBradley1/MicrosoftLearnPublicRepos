<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-data-gcc?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2023-02-17 -->

# Manage data for Microsoft Whiteboard in GCC environments

Note

This guidance applies to US Government Community Cloud \(GCC\) environments.

Data is stored as .whiteboard files in OneDrive for Business. An average whiteboard might be anywhere from 50 KB to 1 MB in size and located wherever your OneDrive for Business content resides. To check where new data is created, see [Microsoft 365 services data locations](https://learn.microsoft.com/en-us/microsoft-365/enterprise/m365-dr-services-data-location). Look at the location for OneDrive for Business. All properties that apply to general files in OneDrive for Business also apply to Whiteboard, except for external sharing.

You can manage Whiteboard data using existing OneDrive for Business controls. For more information, see [OneDrive guide for enterprises](https://learn.microsoft.com/en-us/onedrive/plan-onedrive-enterprise).

You can use existing OneDrive for Business tooling to satisfy data subject requests \(DSRs\) for General Data Protection Regulation \(GDPR\). Whiteboard files can be moved in the same way as other content in OneDrive for Business. However, share links and permissions might not move.

In order to manage data, you must first ensure that Whiteboard is enabled for your organization. For more information, see [Manage access to Whiteboard in GCC environments](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-whiteboard-access-gcc?view=o365-worldwide).

## Data controls supported

The following data controls are currently supported in Whiteboard:

- Retention policies
- Quota
- Legal hold
- Data Loss Prevention \(DLP\)
- Basic eDiscovery: Whiteboards are stored as .whiteboard files in the creator's OneDrive for Business. They're indexed for keyword and file type search, but aren't available to preview/review. Upon export, an admin needs to upload the file back to OneDrive for Business to view the content. More support is planned for the future.

## Data controls planned

The following data controls are planned for future releases of Whiteboard:

- Sensitivity labels
- Analytics
- More eDiscovery support
- Storing whiteboards in SharePoint sites

## See also

[Manage access to Whiteboard - GCC](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-whiteboard-access-gcc?view=o365-worldwide)

[Manage sharing for Whiteboard - GCC](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-sharing-gcc?view=o365-worldwide)

[Manage clients for Whiteboard - GCC](https://learn.microsoft.com/en-us/microsoft-365/whiteboard/manage-clients-gcc?view=o365-worldwide)
