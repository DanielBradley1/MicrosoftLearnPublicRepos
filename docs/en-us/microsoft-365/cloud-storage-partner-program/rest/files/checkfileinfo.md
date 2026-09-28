<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# CheckFileInfo

![Online icon](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-web.png) ![Mobile icon](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The `CheckFileInfo` operation returns information about a file, a user's permissions on that file, and general information about the capabilities that the WOPI host has on the file.

### GET /wopi/files/\(file\_id\)

The `CheckFileInfo` operation is one of the most important WOPI operations. `CheckFileInfo` must be implemented for all WOPI actions. This operation returns information about a file, a user’s permissions on that file, and general information about the capabilities that the WOPI host has on the file. Also, some `CheckFileInfo` properties can influence the appearance and behavior of WOPI clients.

Tip

Some properties aren't supported within the Microsoft 365 - Cloud Storage Partner Program. These operations are marked 🔒 `Not supported in the CSPP`.

### Parameters

- **file\_id** \(*string*\) – A string that specifies a [file ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) of a file managed by the host. This string must be URL safe.

### Query parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host uses to determine whether the request is authorized.

### Request headers

- *X-WOPI-SessionContext* – The value of the [session context](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#session_context), if provided on the initial WOPI action URL.

### Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token).
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found or user unauthorized.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.

In addition to the request and response headers listed here, this operation might also use the Standard WOPI request and response headers. For more information see [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response properties

`CheckFileInfo` response properties are a key way that a WOPI host communicates capabilities and expected behaviors to WOPI clients. Many of the properties in the `CheckFileInfo` response are required. Even properties that are optional provide important ways for the host to direct the end-user client experience.

[Response property reference](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response)

## PostMessage properties for web-based WOPI clients

`CheckFileInfo` supports a number of properties that web-based WOPI clients can use, such as Microsoft 365 for the web to customize the user interface and experience when using those clients. For more information on these properties and how to use them, see [PostMessage properties](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/customization#postmessage-properties).

## CheckFileInfo properties for CSPP Plus

CSPP Plus extends `CheckFileInfo` with additional properties intended to support WOPI+ hosts.

For more information, see [CSPP Plus CheckFileInfo properties](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-csppp).

## Other Properties

These are additional properties supported by `CheckFileInfo` but aren't central to the operation of a WOPI host. Properties that are pre-release and not supported by any WOPI client or have been previously deprecated are also listed here.

For more information on other supported properties, see [Other CheckFileInfo property reference](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other).
