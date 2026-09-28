<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/rename-file-plus -->
<!-- Sitemap-Last-Modified: 2023-03-04 -->

# RenameFile for CSPP Plus

![Desktop](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/cspp-platform-desktop.png)

If a document is held by one or more `Coauth` or `CoauthExclusive` lock references, a valid `Coauth` lock reference must be provided for the call to succeed.

For a full description of the `RenameFile` API, see the existing API contract:

- [RenameFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile)

## Request headers

- `X-WOPI-CoauthLockId` \(string\) – Optional. A string provided by the client that the host must use to identify the `Coauth` lock on the file. Size limit: 1,024 ASCII characters.

## Status codes

- [400 Bad Request](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.1)

  - The specified name is illegal.
  - Occurs when both `X-WOPI-Lock` and `X-WOPI-CoauthLockId` are provided. Only one of the headers should be set.
  - The header size wasn't within the acceptable range.

- [409 Conflict](http://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10)

  - Lock mismatch - The file is locked but the supplied lock type \(X-WOPI-Lock, X-WOPI-CoauthLockId\) or value doesn't match the actual lock on the file.
  - The file is locked, but the client did not supply any lock \(X-WOPI-Lock or X-WOPI-CoauthLockId\)
  - Locked by another interface.

## Next steps

Learn about changes in these methods for WOPI coauthoring extensions:

- [GetCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-lock)
- [UnlockCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/unlock-coauth-lock)
- [RefreshCoauthLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/refresh-coauth-lock)
- [GetCoauthTable](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-coauth-table)
- [WOPI locks](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/wopi-locks)
