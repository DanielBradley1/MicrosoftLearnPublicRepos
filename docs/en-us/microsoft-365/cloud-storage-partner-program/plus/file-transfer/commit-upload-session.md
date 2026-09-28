<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/commit-upload-session -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Commit an upload session

This article describes how to commit an upload session.

## Method

After the data is uploaded for the session, the client can commit that session by using the `PutChunkedFile` method, which passes the session token.

## Success

If the commit is successful, the upload session and associated temporary storage are automatically cleaned up by the host.

## Fail

If the commit fails for an upload session due to coherency failure, the WOPI client can update the upload session by appending new chunks. It will then retry the commit.

## Next steps

- [Create an upload session](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/create-upload-session)
- [Upload bytes to the upload session](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/upload-bytes-session)
