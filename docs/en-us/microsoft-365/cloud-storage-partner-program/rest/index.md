<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ -->
<!-- Sitemap-Last-Modified: 2025-02-10 -->

# WOPI REST API Reference

The Web Application Open Platform Interface Protocol \(WOPI\) defines a set of operations that enable clients to access and change files stored by a server. WOPI is a REST-based protocol. It defines a set of [REST endpoints](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/endpoints) and operations that are run by issuing HTTP requests to those endpoints.

The WOPI protocol is used by Microsoft 365 applications, such as Microsoft 365 for the web, to view and edit files that are stored in a cloud service. Thus, Microsoft 365 for the web is a [WOPI client](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#wopi-client), while the cloud service that stores the files is a [WOPI server](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary#wopi-host--wopi-server), often referred to as a *host*.

This documentation is a reference for all the defined WOPI operations. However, clients don't have to use every operation. WOPI is modular. A WOPI server need only run the operations required by the WOPI client\(s\) that the server intends to integrate with. To learn more about the specific requirements for integrating with Microsoft 365 for the web or Microsoft 365 for mobile, see the following sections:

- [Using the WOPI protocol to integrate with Microsoft 365 for the web](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/)
- [Integrating with Microsoft 365 for mobile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/overview)
