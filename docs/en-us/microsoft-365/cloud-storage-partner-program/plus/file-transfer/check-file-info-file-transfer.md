<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/check-file-info-file-transfer -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# CheckFileInfo and File Transfer Protocol

![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

The new *optional* `SupportsResumableFileTransfer` property enables resumable file transfers included as part of the WOPI coauthoring extensions.

## Implementation

The `SupportsResumableFileTransfer` property is a Boolean value that indicates whether the host supports resumable file transfers. It also implements the following WOPI operations:

- `GetChunks`
- `CreateUploadSession`
- `UpdateUploadSession`

## Next steps

- [GetChunkedFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/get-chunked-file)
- [CreateUploadSession](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/create-upload-session)
