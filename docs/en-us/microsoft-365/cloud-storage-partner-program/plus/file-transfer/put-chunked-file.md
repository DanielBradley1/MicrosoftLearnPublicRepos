<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/put-chunked-file -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# PutChunkedFile

![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

POST /wopi/files/\(file\_id\)/contents

The `PutChunkedFile` operation updates the file's contents.

`PutChunkedFile` supports two types of locks: WOPI lock and `Coauth` lock.

- If the `X-WOPI-Lock` header isn't empty, the WOPI client uses a WOPI Lock.
- If the `X-WOPI-CoauthLockId` header isn't empty, the WOPI client uses `Coauth` lock.
- If both headers are set in a request, the host returns a 400 error.

When a host receives a `PutChunkedFile` request on a file that isn't locked, the host must check the current size of the file. If it's 0 bytes, the `PutChunkedFile` request is valid and should proceed. If it's any value other than 0 bytes, or is missing, the host responds with a "409 Conflict" message. For more information, see [Creating new files using Office for the web](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/createnew).

If the file is currently locked by a WOPI lock and the `X-WOPI-Lock` value doesn't match the lock currently on the file, the host returns a "lock mismatch" response \(409 Conflict\) and includes an `X­WOPI-Lock` response header with the value of the current lock on the file. If the file is unlocked, the host must set `X-WOPI-Lock` to the empty string.

If the file is currently locked by a WOPI lock and the client provides a `Coauth` lock, the host returns a "lock mismatch" response \(409 Conflict\) and includes an `X-WOPI-ConflictingMechanism` response header with a `WOPI-Lock` value. If the file is unlocked, the host must set `X-WOPI-Lock` to an empty string.

If the file is currently locked by `Coauth` lock and the `X-WOPI-CoauthLockId` value isn't in the CoauthTable, the host returns a "lock mismatch" response \(409 Conflict\).

If the file is currently locked by another entity with a `CoauthExclusive` lock, the host returns a "lock mismatch" response \(409 Conflict\) with an empty response body. The `X-WOPI-ConflictingMechanism` header should be set to `WOPI-CoauthExclusiveLock`.

If the file is currently locked by another entity without a WOPI lock or a WOPI `Coauth` lock, the host must return a "lock mismatch" response \(409 Conflict\) with an empty response body. The `X-WOPI-ConflictingMechanism` header should be set to `Other`.

| Host file lock state | Client presented lock | X-WOPI-ConflictingMechanism response header | X-WOPI-Lock response header | Client retry strategy |
| --- | --- | --- | --- | --- |
| Another entity beyond WOPI locks | WOPI lock or `Coauth` or `CoathExclusive` lock | Other | Empty | No retry |
| WOPI lock | Mismatching WPI lock or any `Coauth` or `CoauthExclusive` lock | `WOPI-Lock` | Value of current WOPI lock on the file | No retry |
| WOPI `CoauthExclusive` lock | Any WOPI lock or `Coauth` lock or mismatching `CoauthExclusive` lock | `WOPI-CoauthExclusiveLock` | Empty | No Retry |
| WopiCoauthLock | `CoauthLockId` isn't in `CoauthTable` or is expired | N/A | N/A | Client must send a `GetCoauthLock` request and follow with a `PutChunkedFile` request if the lock is successfully acquired. |

When the client has a valid WOPI, `Coauth`, or `CoauthExclusive` lock, but the sequence number provided by the WOPI client doesn't match the latest value on the host, this is considered a coherency failure. The host must return "412 Precondition Failed" with an empty response body and pass its latest sequence number in the response header.

A new sequence number should be generated and returned in the response header.

## Parameters

- `file_id` \(string\) – Required. A string that specifies the file ID of a file managed by the host. This string must be URL safe.

## Query parameters

- `access_token` \(string\) – Required. An access token that the host uses to determine whether the request is authorized.

## Request headers

- `X-WOPI-Override` \(string\) – Required. The string is `PUT_CHUNKED_FILE`.
- `X-WOPI-SequenceNumber` \(integer\) – Required. An integer value provided by the WOPI client that indicates the sequence number of the state of the file client expects on the host. The value must be greater than 0.
- `X-WOPI-Lock` \(string\) – Optional. A string provided by the WOPI client in a previous lock request.
- `X-WOPI-CoauthLockId` \(string\) – Optional. A string provided by the client that the host must use to uniquely identify the client for the lock on the file. The size limit is 1024 characters. This is the string provided by the client to a `GetCoauthLock` request.
- `X-WOPI-Editors` \(string\) – Optional. A comma-delimited string of `UserId` values that represent the users who contributed changes to the document in the `PutChunkedFile` request. The host must validate the proof-key if this header is set. For a full description of proof-key validation, see [Verify that requests originate from Office for the web by using proof keys](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/proofkeys).

## Request body

Sample message:

```json
{
  "ContentProperties": [],
  "Signatures": [
    {
      "StreamId": "MainContent",
      "ChunkingScheme": "Zip",
      "ChunkSignatures": [
        {
          "ChunkId": "YKWPmdVdMY14qK003yTMXg==",
          "Length": 9999
        },
        {
          "ChunkId": "ZZbM2oyjAXOFHEnVJ7Q2cg//",
          "Length": 6999
        },
        {
          "ChunkId": "==QQQbM2oyjAXOFHEnVJ7Q2cbb",
          "Length": 3999
        }
      ]
    },
    {
      "StreamId": "AlternateStream",
      "ChunkingScheme": "FullFile",
      "ChunkSignatures": [
        {
          "ChunkId": "R3ZBz2Ookt9LmDaePUpB8Q==",
          "Length": 102499
        }
      ]
    }
  ]
}
```

When processing a `PutChunkedFile` request, the host only updates the streams included in the request body `Signatures` array. Other streams for the file are left untouched and carried forward. These unmodified streams are in the updated file at the new sequence number. If the client includes a `Signature` entry with zero chunks for any stream other than `MainContent`, the host deletes the stream.

When the request specifies an upload session via `UploadSessionTokenToCommit`, the host includes the upload session binary stream while processing the request as if it was passed inline in the `PutChunkedFile` request.

## Response headers

- `X-WOPI-SequenceNumber` \(integer\) – Required. An integer value that indicates the latest state of the file on the host. The value must be greater than 0, and should be increased if the host file is updated.
- `X-WOPI-ItemVersion` \(string\) – Required. A string value that indicates the file version. Its value should be the same as the `Version` value in `CheckFileInfo`.
- `X-WOPI-FailureReason` \(string\) – Optional. Used for logging purposes only. It should be set for non-200 OK responses.
- `X-WOPI-Lock` \(string\) – Optional. A string value that identifies the current lock on the file. This header must always be included when responding to the request with "409 Conflict" and when the file is locked by a WOPI Lock. Don't include it when responding to the request with "200 OK".
- `X-WOPI-ConflictingMechanism` \(string\) – Optional. A string value that indicates the current lock on the file. This value must be set when responding to the request with "409 Conflict" due to lock mismatch. Don't include it when responding to the request with "200 OK". Valid values of this header are `WOPI-Lock`, `WOPI-CoauthExclusiveLock`, and `Other`.

## Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

  - The required parameters were not provided.
  - The request was incorrectly formatted.
  - Both X-WOPI-Lock and X-WOPI-CoauthLockId were provided.
  - The host does not have a ChunkId but the WOPI client did not pass any chunk payload.
  - Frames in request stream cannot be deserialized properly.
  - X-WOPI-Editors header is set but proof-key is not correctly signed.
  - Client did not include MainContent StreamId in the request
  - The header size was not within the acceptable range.

- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid access token.
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized.
- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10)

  - The resource is exclusively locked using a different locking mechanism \(other than WOPI/`Coauth` locks\).
  - The resource is exclusively locked by another entity using a different lock type \(WOPI versus `Coauth`\). This failure would be indicated by X-WOPI-Lock response header.
  - The resource is exclusively locked by another entity using `CoauthExclusiveLock` \(`Coauth` versus `CoauthExclusive`\). This failure would be indicated by X-WOPI- ConflictingMechanism response header.

- [412 Precondition Failed](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.13)

  - The sequence number provided by WOPI client does not match the state of the document on the host. The current sequence number of the file on the host must be provided in the X WOPI SequenceNumber response header in this case.

- [413 Request Entity Too Large](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.14) – File is too large; the maximum file size is host-specific.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

The maximum number of alternate streams \(streams other than `MainContent`\) supported for a given file at any time is 256. An alternate stream will expire 30 days after it was last updated.

The maximum number of unexpired content properties supported for a given file at any time is 256. A content property will expire 30 days after it was last updated.

## Next steps

[GetSequenceNumber](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-sequence-number)
