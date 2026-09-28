<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# PutRelativeFile

![Online icon](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-web.png) ![iOS and Android](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/images/cspp-platform-mobile.png) ![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The `PutRelativeFile` operation creates a new file on the host based on the current file.

### POST \(/wopi/files/\(file\_id\)

The `PutRelativeFile` operation creates a new file on the host based on the current file. The host must use the content in the [POST](https://tools.ietf.org/html/rfc7231#section-4.3.3) body to create a new file.

The `PutRelativeFile` operation has two distinct modes: *specific* and *suggested*. The primary difference between the two modes is whether the WOPI client expects the host to use the file name provided exactly \(*specific* mode\) or if the host can adjust the file name in order to make the request succeed \(*suggested* mode\).

Hosts can determine the mode of the operation based on which of the mutually exclusive **X-WOPI-RelativeTarget** \(indicates *specific* mode\) or **X-WOPI-SuggestedTarget** \(indicates *suggested* mode\) request headers is used. The expected behavior for each mode is described in detail below.

The `PutRelativeFile` operation might be called on a file that is not locked, so the **X-WOPI-Lock** request header is not included in this operation. An example of when this might occur is if a user uses the *Save As* feature when viewing a document in read-only mode. The source file won't be locked in this case, but the `PutRelativeFile` operation is invoked on it.

However, a file matching the target name might be locked, and in *specific* mode, the host must respond with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) and include a **X-WOPI-Lock** response header as described below.

Important

If a WOPI host sets the [SupportsUpdate](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsupdate) property in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) to `true`, the host is expected to implement the `PutRelativeFile` operation. However, a host might choose not to implement this operation even though [SupportsUpdate](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsupdate) is `true` and they must do the following:

1. Set the [UserCanNotWriteRelative](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#usercannotwriterelative) property to `true` always.
2. Return a [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) to all `PutRelativeFile` requests.

#### Excel for the web

Excel for the web uses this operation in the following two ways:

- As part of the **Save As** feature. If `PutRelativeFile` is not supported, the **Save As** feature doesn't work in Excel for the web.
- To support editing of some Excel files in Excel for the web. Some files might contain content that's not currently supported in Excel for the web. In this case, Excel for the web prompts a user to save an editable copy of the document, removing all unsupported content. The file can then be edited in Excel for the web. If `PutRelativeFile` isn't supported, files with unsupported content aren't editable in Excel Online.

### Parameters

- **file\_id** \(*string*\) – A string that specifies a [file ID](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) of a file managed by host. This string must be URL safe.

### Query parameters

- **access\_token** \(*string*\) – An [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) that the host uses to determine whether the request is authorized.

### Request headers

- *X-WOPI-Override* – The **string** `PUT_RELATIVE`. This header is required.
- *X-WOPI-SuggestedTarget* –

  A UTF-7 encoded **string** specifying either a file extension or a full file name, including the file extension. Hosts can differentiate between full file names and extensions as follows:

  - If the string begins with a period \(`.`\), it's a file extension.
  - Otherwise, it's a full file name.


  If only the extension is provided, the name of the initial file without extension should be combined with the extension to create the proposed name.


  The response to a request including this header must never result in a [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) or [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). Rather, the host must modify the proposed name as needed to create a new file that's both legally named and doesn't overwrite any existing file, while preserving the file extension.


  This header must be present if **X-WOPI-RelativeTarget** is not present. The two headers are mutually exclusive. If both headers are present, the host should respond with a [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) or [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2).


  - *X-WOPI-RelativeTarget* –

    A UTF-7 encoded **string** that specifies a full file name including the file extension. The host must not modify the name to fulfill the request.

    If the specified name is illegal, the host must respond with a [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1).

    If a file with the specified name already exists, the host must respond with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10), unless the **X-WOPI-OverwriteRelativeTarget** request header is set to `true`. When responding with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) for this reason, the host might include an **X-WOPI-ValidRelativeTarget** specifying a file name that's valid.

    If the **X-WOPI-OverwriteRelativeTarget** request header is set to `true` and a file with the specified name already exists and is locked, the host must respond with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) and include an **X-WOPI-Lock** response header containing the value of the current lock on the file.

    This header must be present if **X-WOPI-SuggestedTarget** is not present. The two headers are mutually exclusive. If both headers are present, the host should respond with a [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) or [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2).

- *X-WOPI-OverwriteRelativeTarget* –

  A **Boolean** value that specifies whether the host must overwrite the file name if it exists. The default value is `false`. In other words, if **X-WOPI-OverwriteRelativeTarget** is not explicitly included on the request, hosts must behave as though its value is `false`.

  This header is only valid if the **X-WOPI-RelativeTarget** is also included on the request. It must be ignored in all other cases.

  If the user is not authorized to overwrite the target file, the host must respond with a [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2).
- *X-WOPI-Size* – An **integer** that specifies the size of the file in bytes.
- *X-WOPI-FileConversion* –

  A header whose presence indicates that the request is being made in the context of a [binary document conversion](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/conversion). This header is only included on the request in that case. Thus, if **X-WOPI-FileConversion** isn't explicitly included on the request, hosts must behave as if the `PutRelativeFile` request is not being made as part of a binary document conversion.

  For more information on the conversion process and how to use this header, see [Editing binary document formats](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/conversion).

### Request body

The request body must be the full binary contents of the file.

### Response headers

- *X-WOPI-ValidRelativeTarget* – A UTF-7 encoded **string** that specifies a full file name including the file extension. This header might be used when responding with a [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10), because a file with the requested name already exists, or when responding with a [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1), because the requested name contained invalid characters. If this response header is included, the WOPI client should automatically retry the `PutRelativeFile` operation using the contents of this header as the **X-WOPI-RelativeTarget** value and shouldn't display an error message to the user.
- *X-WOPI-Lock* – A **string** value identifying the current lock on the file. This header must always be included when responding to the request with [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). It shouldn't be included when responding to the request with [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1).
- *X-WOPI-LockFailureReason* – An optional **string** value indicating the cause of a lock failure. This header might be included when responding to the request with [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10). There's no standard for how this string is formatted, and it must only be used for logging purposes.
- *X-WOPI-LockedByOtherInterface* –

  ***Deprecated: Deprecated since version 2015-12-15:*** This header is deprecated and should be ignored by WOPI clients.

### Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1) – Specified name is illegal.
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token).
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found or user unauthorized.
- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) – Target file already exists or the file is locked. If the target file is locked, you must include an **X-WOPI-Lock** response header containing the value of the current lock on the file.
- [413 Request Entity Too Large](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.14) – File is too large. The maximum size is host-specific.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported. If the host sets the [SupportsUpdate](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportsupdate) and `UserCanNotWriteRelative` properties to `true` in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo), you must use this response code when this operation is called.

In addition to the request and response headers listed here, this operation might also use the Standard WOPI request and response headers. For more information see [Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers).

## Response

The response to a `PutRelativeFile` call is [JSON](https://tools.ietf.org/html/rfc4627.html) containing a number of properties, some of which are optional.

All optional values default to the following values based on their type:

| Type | Default value |
| --- | --- |
| Boolean | `false` |
| String | The empty string |
| Integer/Long | Varies; see individual properties for details |
| Array | Empty array |

Important

No properties should be set to `null`. If you don't wish to set a property, simply omit it from the response and WOPI clients then use the default value.

### Required response properties

The following properties must be present in all `PutRelativeFile` responses:

- **Name** \(*string*\) - The name of the file, including extension, without a path.
- **Url** \(*string*\) - A URI of the form `http://server/<...>/wopi/files/(file_id)?access_token=(access token)`, of the newly created file on the host. This URL is the [WOPISrc](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#wopisrc) for the new file with an [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) appended. Or, stated differently, it's the URL to the host’s Files endpoint for the new file, along with an [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token). A [GET](https://tools.ietf.org/html/rfc7231#section-4.3.1) request to this URL invokes the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) operation.

  Caution

  This property includes an [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) so it has important security implications. For more information, see [Preventing ‘token trading’](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/security#preventing-token-trading).

### Optional response properties

Following are the optional response properties.

- **HostViewUrl** - The [HostViewUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostviewurl), as a **string**, for the newly created file.
- **HostEditUrl** - The [HostEditUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#hostediturl), as a **string**, for the newly created file.
