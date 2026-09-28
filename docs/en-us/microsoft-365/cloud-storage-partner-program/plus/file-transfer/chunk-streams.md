<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/chunk-streams -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Chunk streams

To achieve incremental file transfer, the file contents are broken into chunks. How a binary stream is broken into chunks depends on the chunking scheme. The chunks constructed to be sent in the request or response stream may appear in any order. The file signature should be used to determine the order of the chunks.

Two chunking schemes are supported:

- `Zip` – Applicable to zip files, which are the default format of Office files that support coauthoring.
- `FullFile` – Applicable to encrypted Office files. The full binary contents of the given stream are represented as a single chunk.

The host must support all of the chunking schemes. Zip chunking is the preferred scheme, except in scenarios with encrypted files that aren't in zip format.

## ChunkId

Chunks are identified by `ChunkId`, which is the hash \(128-bit Spooky hash\) of the chunk binary payload.

## File signature

The ordered list of `ChunkId` identifiers and the length of all the chunks for a given file. The file signature is designed to self-describe the full content of the file.

## Request to get delta changes

1. Select the `chunkingScheme` option based on the file content.
2. Send a list of `ChunkId` identifiers that are already known to the WOPI client.

## Response to get delta changes

1. Select the `chunkingScheme` option based on the file content.
2. Chunk the binary file contents based on `chunkingScheme`.
3. Compute `ChunkId` for each chunk and generate a file signature.
4. Decode the list of known chunks in the request.
5. Send the file signature and the chunks referred to in the file signature that are not in the request's list of known chunks.

## Request to update file based on delta changes

1. Select the `chunkingScheme` option based on the file content.
2. The WOPI client chunks the updated binary file based on `chunkingScheme`.
3. Generate a new file signature.
4. Compare the new file signature with the last known file signature.
5. Send the new file signature and the chunks referred in the new file signature that aren't in the last known file signature.

## Applying the delta changes

1. Select the `chunkingScheme` option based on the file content.
2. Chunk the base file based on `chunkingScheme`.
3. Assemble the new list of chunks based on the file signature, base file chunks, and delta chunks.
4. Write all the valid chunks in the order provided by the file signature you received. This step doesn't require any zip semantics.

## Next steps

- [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/check-file-info-file-transfer)
- [GetChunkedFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-chunked-file)
