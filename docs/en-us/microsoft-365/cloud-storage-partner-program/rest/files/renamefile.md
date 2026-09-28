<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# RenameFile

![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The `RenameFile` operation renames a file.

## POST /wopi/files/\(file\_id\)

Important

Renaming the file must not cause the [File ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id), and by extension, the [WOPISrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc), to change.

If the host can't rename the file because the name requested is invalid or conflicts with an existing file, the host should try to generate a different name based on the requested name that meets the file name requirements.

If the host can't generate a different name, it should return an HTTP status code [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1). The response must include an **X-WOPI-InvalidFileNameError** header that describes why the file name was invalid.

If the file is currently unlocked, the host should respond with a [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) and proceed with the rename.

If the file is currently locked and the **X-WOPI-Lock** value doesn't match the lock currently on the file the host must return a *lock mismatch* response \([409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10)\) and include an **X-WOPI-Lock** response header containing the value of the current lock on the file.

Tip

Microsoft 365 for the web includes contains UI that users can use to rename files. In order to activate this UI in Office for the web, you must implement the RenameFile operation, and also do the following:

- Set [**SupportsRename**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsrename) and [**UserCanRename**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#usercanrename) to `true` in your [**CheckFileInfo**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response.
- Set a [**FileNameMaxLength**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#filenamemaxlength) value if the default value isn't correct for your WOPI host.

### Parameters

- **file\_id** \(*string*\) – A string that specifies a [file ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) of a file managed by host. This string must be URL safe.

### Query parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host uses to determine whether the request is authorized.

### Request headers

- *X-WOPI-Override* – The **string** `RENAME_FILE`. This header is required.
- *X-WOPI-Lock* – A **string** provided by the WOPI client that the host uses to identify the lock on the file.
- *X-WOPI-RequestedName* – A UTF-7 encoded **string** that's a file name, *not including the file extension.*

### Response headers

- *X-WOPI-InvalidFileNameError* – A **string** describing the reason the rename operation couldn't be completed. This header should only be included when the response code is [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1). This value must only be used for logging purposes.
- *X-WOPI-Lock* – A **string** value identifying the current lock on the file. This header must always be included when responding to the request with [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). It shouldn't be included when responding to the request with [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1).
- *X-WOPI-LockFailureReason* – An optional **string** value indicating the cause of a lock failure. This header might be included when responding to the request with [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). There's no standard for how this string is formatted, and it must only be used for logging purposes.
- *X-WOPI-LockedByOtherInterface* –

  ***Deprecated: Deprecated since version 2015-12-15:*** This header is deprecated and should be ignored by WOPI clients.

### Status Codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) – Specified name is illegal.
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token).
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found or user unauthorized.
- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) – Lock mismatch or locked by another interface. You must always include an **X-WOPI-Lock** response header containing the value of the current lock on the file when using this response code.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

In addition to the request and response headers listed here, this operation might also use the Standard WOPI request and response headers. For more information, see [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response

The response to a `RenameFile` call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing a single required property:

- **Name** \(*string*\) - The name of the renamed file *without a path or file extension.*

  Important

  The **Name** property returned can't include the file extension. This is different than other similar WOPI operations such as [**PutRelativeFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile) and [**CreateChildFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildfile#createchildfile).
