<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/create-upload-session -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# Create an upload session

To begin uploading a set of chunks, the client must first request a new upload session. This creates a temporary storage location where the bytes of the chunks are saved until the complete chunk payload is uploaded.

## Upload session binary stream

The binary stream for an upload session is a collection of chunks \(`FullChunk`\) encoded in similar way as `PutChunkedFile`, where a list of chunks to be uploaded is encoded by using `Frames`. Make sure there isn't `MessageJSON` at the beginning or `EndFrame` at the end.

![Upload session binary stream illustration](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/images/upload-session-binary-stream.png)

## CreateUploadSession

POST /wopi/files/\(file\_id\)

### Parameters

- `file_id (string)` – Required. A string that specifies a file ID of a file managed by the host. This string must be URL safe.

### Query parameters

- `access_token` \(string\) – Required. An access token that the host uses to determine whether the request is authorized.

### Request headers

- `X-WOPI-Override` \(string\) – Required. The string is `CREATE_UPLOAD_SESSION`.

The response to this request provides the details of the newly created `UploadSession`, which includes the `sessiontoken` string used for uploading the parts and the expiry time for the upload session. This session token must be a unique identifier tied to this specific upload session. A given user ID might have more than one upload session active at a time. Every upload session has a 30-minute expiry interval from the time it was last updated.

### Response headers

- `X-WOPI-FailureReason` \(string\) – Optional. Used for logging purposes only. It should be set on non-200 OK responses.

### Response body

The response is [JSON](https://tools.ietf.org/html/rfc4627.html) containing the following required properties:

- `UploadSessionToken` – A string identifier for the newly created upload session. This is used to reference the upload session for any future operations.

Sample response:

```json
{
  "UploadSessionToken": "sessiontoken"
}
```

### Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid access token.
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

## Next steps

- [Upload bytes to the upload session](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/upload-bytes-session)
- [Commit an upload session](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/commit-upload-session)
