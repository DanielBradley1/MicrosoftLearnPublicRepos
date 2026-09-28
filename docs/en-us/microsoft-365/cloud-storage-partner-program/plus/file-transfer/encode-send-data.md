<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/encode-send-data -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Encode and send data on the wire

This article explains how to encode and send data on the wire.

## Frame protocol for sending chunks

The request/response payload is broken into frames to send the chunks. Each frame has a header that declares its frame type, extended header size, payload size, and extended header. All binary structures must be provided in big-endian byte order.

![Illustration of byte order](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/images/byte-order.png)

### Frame type

Four frame types are supported:

- `MessageJSON` – Must be the first frame; contains request or response-body structured data serialized via JSON.
- `Chunk` – Contains the full binary content for a given chunk. `ChunkId` is stored in the extended header field, and chunk data bytes are stored in the frame payload.

  - Frame Extended Header – Used for additional data for `Chunk` and `ChunkRange` frames.
  - Frame Payload – The frame payload is all the data in binary format.

- `ChunkRange` - Contains the partial binary content for a chunk. `ChunkId`, `offset`, `length`, and `Flags` are stored in the extended header field, and chunk data bytes are stored in the frame payload.
- `EndFrame` – Must be the last frame; indicates the end of the request payload.

The table lists all frame types and expected values for the fields:

| FrameType Name | FrameType | ExtendedHeader Size | Payload Size | Extended Header Contents | Extended Header Encoding | Frame Payload |
| --- | --- | --- | --- | --- | --- | --- |
| `MessageJSON` | 2 | 0 | 64-bit integer | Empty | N/A | Structured data applicable to that request or response |
| `Chunk` | 3 | 16 | 64-bit integer | `ChunkId` \(128-bit spooky hash\) | Raw bytes | All chunk data bytes |
| `ChunkRange` | 4 | 36 | 64-bit integer | - ChunkId \(16 bytes\)<br>- Offset \(64-bit unsigned integer\)<br>- Length \(64-bit unsigned integer\)<br>- Flags \(32-bit unsigned integer; indicates `EndOfChunk` | Raw bytes \(all numbers in big-endian byte order\) | Chunk range bytes |
| `EndFrame` | 1 | 0 | 0 | Empty | N/A | Empty |

ChunkRange extended header: This data is laid out in bytes as detailed in the preceding table. For the Flags field, these are the only valid values \(for the 32-bit unsigned integer\) currently:

- 0 - Indicates a `ChunkRange` between the chunk.
- 1 – Indicates the `ChunkRange`, which includes the end of the chunk.

## Upload request stream example for zip archive file

![Upload request stream example for zip archive file](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/images/upload-request-zip.png)

## Upload request stream example for non-zip archive file

![Upload request stream example for non-zip archive file](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/images/upload-request-non-zip.png)

Sample `PutChunkedFile` MessageJSON for a non-zip archive file:

```json
{
  "ContentProperties": [],
  "Signatures": [
    {
      "StreamId": "MainContent",
      "ChunkingScheme": "FullFile",
      "ChunkSignatures": [
        {
          "ChunkId": "P4oXyRH4V/AHALoD7GZ9Yw==",
          "Length": 199999
        }
      ]
    },
    {
      "StreamId": "Alternate",
      "ChunkingScheme": "FullFile",
      "ChunkSignatures": [
        {
          "ChunkId": "YKWPmdVdMY14qK003yTMXg==",
          "Length": 2999
        }
      ]
    }
  ],
  "UploadSessionTokenToCommit": null
}
```

GetChunks response stream example for zip archive file:

![GetChunks response stream example for zip archive file](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/images/response-stream-zip.png)

Note

The `MessageJSON` for all the requests and responses are encoded by using JSON.

## Next steps

Learn about [Multi-request file uploads](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/multi-request-file-upload-overview).
