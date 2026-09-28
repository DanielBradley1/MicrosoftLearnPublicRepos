<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-chunked-file -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetChunkedFile

![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

`POST /wopi/files/(file_id)`

The `GetChunkedFile` operation retrieves the chunks for the file from the host. If the WOPI client already has a version of the file, it passes the list of `ChunkId` identifiers for already known chunks to the host.

Clients can use the `ContentFilters` filter to indicate which chunks are returned by the host.

The host needs to check if the file is a zip archive by following the [ZIP File Format Specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT).

- If the file is not a zip archive, treat the full binary content of the given stream as a single chunk, and pass the file signature and the single chunk in the response body.
- If the file is a zip archive file and the client hasn't presented the list of known chunk IDs, pass the file signature and data for all chunks in the response body.
- If the file is a zip archive and the client presents the known chunk IDs, the host needs to compare the client's known chunk IDs passed in the request body with their own file signature. Then the host returns chunks not in the list.

In all of these cases, the host must pass a sequence number in the response header.

## Parameters

- `file_id` \(string\) – Required. A string that specifies a file ID of a file managed by the host. This string must be URL safe.

## Query parameters

- `access_token` \(string\) – Required. An access token that the host uses to determine whether the request is authorized.

## Request headers

- `X-WOPI-Override` \(string\) – Required. The string is `GET_CHUNKED_FILE`.

## Request body

Sample message:

```json
{
  "ContentPropertiesToReturn": [
    "prop1",
    "prop2"
  ],
  "ContentFilters": [
    {
      "AlreadyKnownChunks": [
        "R3ZBz20okt9LmDaePUpB8Q=="],
      "ChunkingScheme": "Zip",
      "StreamId": "MainContent",
      "ChunksToReturn": "All"
    },
    {
      "AlreadyKnownChunks": [],
      "ChunkingScheme": "FullFile",
      "StreamId": "AltStream",
      "ChunksToReturn": "All"
    }
  ]
}
```

## Required request properties

The following properties must be present in all GetChunkedFile requests:

### ContentPropertiesToReturn

This is a required property, but it can be an empty list.

### ContentFilters

This allows the WOPI client to filter which streams and which chunks within those streams should be returned. This does not impact the `MessageJSON` frame returned, which will always contain the full signature of each stream being requested.

This should at least have one entry.

Valid values for `ChunksToReturn`:

- `All` – Receive all chunks that are not in the list of AlreadyKnownChunkIds. This is the default.
- `None` – Do not receive any chunk data.
- `LastZipChunk` – Receive only the last chunk of a zip archive. If the file is not a zip archive, this value behaves the same as `None`. If the host can't support zip chunking for the given file, treat this value as `None`.

The host only returns streams requested via `ContentFilters`. There is no way for the client to get all the streams without knowing the `StreamId` value in advance. In addition, there should only by one `ContentFilter` entry per `StreamId`. Otherwise, the host returns a 400 error. There should be at least one entry in the `ContentFilters` element. Otherwise, the request fails with a 400 return code. If the requested `StreamId` doesn't exist on the host, the request succeeds. In this case, the host returns a `Signature` entry with zero chunks in the MessageJSON. In this case, the ChunkingScheme should be set to 'Zip'. Anywhere `ChunkId` is used in a MessageJSON frame \(`ChunkId` or `AlreadyKnownChunks`\), the raw 16-byte spooky hash is encoded by using "Base64 encoding” \(C# equivalent: `System.Convert.ToBase64String()`\).

Note

The `MainContent` stream should always exist after the file is created. It can be a zero-byte stream, which is represented as a `ChunkSignatures` array with one item. The `ChunkId` value for the zero-length item should be the Spooky hash of a zero-byte array.

## Response headers

- `X-WOPI-SequenceNumber` \(integer\) – Required. An integer value that indicates the state of the file on the host. The value must be greater than 0, and should be increased if the host file is updated.
- `X-WOPI-ItemVersion` \(string\) – Required. A string value that indicates the file version. Its value should be the same as the `Version` value in `CheckFileInfo`.
- `X-WOPI-FailureReason` \(string\) – Optional. Used for logging purposes only. Set this value on non-200 OK responses.

## Response body

If the host returns file contents to clients, data is encoded in the response body. The response body is composed of a list of frames. The first frame is `MessageJSON`, which contains the encoded file signature. File chunks are encoded to subsequent chunk frames. The response body stream ends with `EndFrame`.

Sample message:

```json
{
  "ContentProperties": [
    {
      "Retention": "KeepOnContentChange",
      "Name": "prop1",
      "Value": "los"
    },
    {
      "Retention": "DeleteOnContentChange",
      "Name": "prop2",
      "Value": "los"
    },
  ],
  "Signatures": [
    {
      "StreamId": "MainContent",
      "ChunkingScheme": "Zip",
      "ChunkSignatures": [
        {
          "ChunkId": "R3ZBz20okt9LmDaePUpB8Q--",
          "Length": 4096
        },
        {
          "ChunkId": "ZZbM20yjAXOFHEnVJ7Q2cg//",
          "Length": 29999
        }
      ]
    },
    {
      "StreamId": "AltStream",
      "ChunkingScheme": "FullFile",
      "ChunkSignatures": [
        {
          "ChunkId": "Y/bM2oyjAXOFHEnVJ7Q2cg==",
          "Length": 4096
        }
      ]
    }
  ]
}
```

## Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success.
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

  - The request was incorrectly formatted.
  - Frames in request stream cannot be deserialized properly.
  - The header size was not within the acceptable range.

- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid access token.
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

## Next steps

- [GetChunks](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-chunks)
- [PutChunkedFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/put-chunked-file)
