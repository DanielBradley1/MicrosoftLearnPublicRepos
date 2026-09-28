<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/upload-bytes-session -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Upload bytes to an upload session

To upload a set of chunks, the client makes an `UpdateUploadSession` request by passing the session token value received in the `createUploadSession` response. You can upload the entire chunk frame payload, or split it into multiple byte ranges. The byte ranges of individual upload payloads are not required to align to frame chunks within the overall upload session binary stream.

The upload session binary stream fragments must be uploaded in order. Uploading fragments out of order results in an error. If the content range offset of the request is not equal to the total number of bytes that have already been sent in previous requests for a session, the request fails with a "400 - Bad request" error.

If the request body length doesn't match `X-WOPI-ContentRangeLength`, the request fails with a "400 - Bad request" error.

After every successful update, the host extends the upload session expiry time by 30 minutes.

## UpdateUploadSession

`POST /wopi/files/(file_id)`

### Parameters

- `file_id` \(string\) – Required. A string that specifies a file ID of a file managed by the host. This string must be URL safe.

### Query parameters

- `access_token` \(string\) – Required. An access token that the host uses to determine whether the request is authorized.

### Request headers

- `X-WOPI-Override` \(string\) – Required. The string is `UPDATE_UPLOAD_SESSION`.
- `X-WOPI-UploadSessionToken` \(string\) – Required. A string identifier for the upload session that's being updated.
- `X-WOPI-ContentRangeOffset` \(long\) – Required. A long value \(64-bit signed integer\) that represents the offset within the upload session stream this request starts at.
- `X-WOPI-ContentRangeLength` \(long\) – Required. A long value \(64-bit signed integer\) that indicates the length of the content being sent in the body.

### Request body

The request body must be the full binary contents of the part of the request stream being sent.

### Response headers

- `X-WOPI-UploadSessionCurrentOffset` \(long\) – Required. A long value \(64-bit signed integer\) that represents the current offset within the upload session stream next request starts at.
- `X-WOPI-FailureReason` \(string\) – Optional. Used for logging purposes only. It should be set on non-200 OK responses.

### Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

  - The content range offset of the request is not equal to the total number of bytes that have already been sent in previous requests for this session.
  - Request body length does not match X-WOPI-ContentRangeLength.
  - The header size was not within the acceptable range.

- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid access token.
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized.
- [410 Gone](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.11) – Upload session token is invalid \(for example, the upload session expired\).
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

## Next steps

- [Create an upload session](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/create-upload-session)
- [Commit an upload session](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/commit-upload-session)
