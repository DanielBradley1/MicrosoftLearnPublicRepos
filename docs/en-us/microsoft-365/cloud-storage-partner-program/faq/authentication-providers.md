<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/authentication-providers -->
<!-- Sitemap-Last-Modified: 2026-07-10 -->

# What authentication providers does Microsoft 365 for the web support?

Microsoft 365 for the web does not do any authentication. Hosts are expected to handle authentication and authorization by providing WOPI [access tokens](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token). All user-related information is provided to Microsoft 365 for the web by the host using properties in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo).
