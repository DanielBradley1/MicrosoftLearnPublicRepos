<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/multi-request-file-upload-overview -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Multi-request file uploads

Clients can create an upload session to allow large upload payloads to be broken up and transferred to the host over multiple requests. Requests must provide the payload in sequential order. Each request resumes, in byte order, where the previous request finished. The upload session payload contains only chunk frames, and the entire upload session is referred to by a final `PutChunkedFile` call that contains all of the frames in the upload session. If the `PutChunkedFile` call fails \(such as in the case of a sequence number mismatch\), the upload session remains, allowing the client to try a new `PutChunkedFile` call without having to retransmit the entire upload session payload.

To upload a set of chunks using an upload session, follow the steps in these articles:

- [Create an upload session](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/create-upload-session)
- [Upload bytes to the upload session](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/upload-bytes-session)
- [Commit an upload session](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/commit-upload-session)
