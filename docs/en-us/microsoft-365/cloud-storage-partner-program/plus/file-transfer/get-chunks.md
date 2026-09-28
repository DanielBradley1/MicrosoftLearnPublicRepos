<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-chunks -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# GetChunks

![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

`POST /wopi/files/(file_id)`

The `GetChunks` operation allows clients to download specific chunks from the host. Clients can pass a list of `ChunkRange` values to be returned.

In response to the request, the host returns the sequence number along with the chunk data.

If the file on the host changes while the client is downloading the chunks, the client can detect the change by reading an updated sequence number in the response header. The host returns the list of actual chunks being returned in the response body `MessageJSON`. If the file is updated on the host, some of the requested chunks might no longer be valid. The `X-WOPI-SequenceNumber` header must be provided to reflect the latest host state.

## Parameters

- `file_id` \(string\) – Required. A string that specifies a file ID of a file managed by the host. This string must be URL safe.

## Query parameters

- `access_token` \(string\) – Required. An access token that the host uses to determine whether the request is authorized.

## Request headers

- `X-WOPI-Override` \(string\) – Required. The string is `GET_CHUNKS`.

## Request body

Sample message:

```json
{
  "ContentFilters": [
    {
      "StreamId": "MainContent",
      "ChunkingScheme": "Zip",
      "ChunkRangesToReturn": [
        {
          "ChunkId": "ZZbM2oyjAXOFHEnVJ7Q2cg//",
          "Offset": 0,
          "Length": 4096
        },
        {
          "ChunkId": "--QQQbM2oyjAXOFHEnVJ7Q2cbb/",
          "Offset": 4096,
          "Length": -1
        }
      ]
    }
  ]
}
```

Note

Setting the `Length` value of `ChunkRangeToReturn` to -1 indicates that the client is requesting the chunk data from `Offset` to the end of the chunk.

## Status codes

- [200 OK](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.2.1) – Success
- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

  - The request was incorrectly formatted.
  - Frames in request stream can't be deserialized properly.
  - The header size wasn't within the acceptable range.

- [401 Unauthorized](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.2) – Invalid access token.
- [404 Not Found](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.5) – Resource not found/user unauthorized.
- [500 Internal Server Error](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.1) – Server error.
- [501 Not Implemented](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.5.2) – Operation not supported.

## Response headers

- `X-WOPI-SequenceNumber` \(integer\) – Required. An integer value that indicates the latest state of the file on the host. The value must be greater than 0, and should be increased if the host file is updated.
- `X-WOPI-ItemVersion` \(string\) – Required. A string value that indicates the version of the file. Its value should be the same as the `Version` value in `CheckFileInfo`.
- `X-WOPI-FailureReason` \(string\) – Optional. Used for logging purposes only. It should be set on non-200 OK responses.

## Response body

Sample message:

```json
{
  "ChunkRangeCollection": [
    {
      "StreamId": "MainContent",
      "ChunkIds": [
        "==QQQbM2oyjAXOFHEnVJ7Q2cbb/",
        "ZZbM2oyjAXOFHEnVJ7Q2cg//"
      ]
    }
  ]
}
```

The response body is composed of `MessageJSON`, several `PartialChunk` frames, and `EndFrame`. The `ChunkId` values of the chunks that are passed in subsequent `PartialChunk` frames are encoded in `MessageJSON`. This can facilitate asynchronous processing on the receiver. Chunk data is encoded in `PartialChunk` frames. Each frame contains the binary content for a chunk range. `ChunkId`, `offset`, `length` of a partial chunk, and `flag` \(`EndOfChunk`\) are stored in the extended header field, and data bytes are stored in the frame payload. The response body ends with `EndFrame`.

The response body encoding protocol is introduced in this section.

## Next steps

- Learn about [PutChunkedFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/put-chunked-file).
- Learn about [GetSequenceNumber](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-sequence-number).
