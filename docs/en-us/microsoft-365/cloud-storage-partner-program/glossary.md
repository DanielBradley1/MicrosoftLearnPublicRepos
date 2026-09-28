<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/glossary -->
<!-- Sitemap-Last-Modified: 2025-02-10 -->

# Glossary

### WOPI client

A WOPI client is an application or service that runs WOPI operations on a WOPI server by issuing HTTP requests to the WOPI server's WOPI endpoints. Microsoft 365 for the web is an example of a WOPI client.

### WOPI host / WOPI server

A WOPI server, often called a WOPI host or just simply a host, is an application or service that implements WOPI endpoints and operations as described in this documentation, such as [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) and [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile). OneDrive for Business is an example of a WOPI host.

### Broadcast

A broadcast is a special Microsoft 365 for the web scenario where navigation through a document is driven by one or more presenters. A set of attendees can follow along with the presenter remotely.

Note

See also `present`, `attend`

### Host Page

The host page \(also called the *host frame* or *outer frame*\) is the HTML page that hosts an iframe, which points to an Microsoft 365 for the web application.

For more information, see [Building a host page](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/hostpage).

### Session Context

The Session Context is an optional parameter that a host can include on a WOPI request. It's a **string** that's passed to Microsoft 365 for the web in the `sc` query string parameter. If included on a WOPI request, Microsoft 365 for the web returns the value of `sc` as the value of the **X-WOPI-SessionContext** HTTP header when making the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) and [CheckFolderInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/onenote) WOPI requests.

### Server-only open

Open operations for which the local file on disk isn't used \(or isn't present\) and Microsoft 365 communicates only with the service.

### Local-only open

Open operations without coauthoring support for which Microsoft 365 is writing and reading only to and from the local file on disk.

### MRU

Most recently used list. A list of recently used files that shows up when you first start an Microsoft 365 app in the *backstage*.
