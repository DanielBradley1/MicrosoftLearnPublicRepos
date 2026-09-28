<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/wopi-requirements -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# WOPI set up requirements for Microsoft 365 for the web integration

A WOPI host doesn't need to implement every WOPI operation. WOPI hosts express their capabilities using [properties in CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo), such as [SupportsLocks](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#supportslocks). Also, WOPI actions specify the WOPI operations that must be supported in order to use that action, in the form of [Action requirements](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#action-requirements).

But practically speaking, there's a minimum set of operations required to support the two major Office for the web WOPI scenarios - viewing and editing.

Important

While the following lists cover the WOPI operations to be implemented, hosts must also provide [**file IDs**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) and [**access tokens**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token) as part of a basic WOPI implementation.

## View

In order to support viewing documents using Microsoft 365 for the web, WOPI hosts implement:

- [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo)
- [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile)

Important

[**GetFile**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile) must be implemented even if a host is using the [**FileUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileurl) property.

## Edit

In order to support editing documents using Microsoft 365 for the web, WOPI hosts implement:

- [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo)
- [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile)
- [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile)
- [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile)
- [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock)
- [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock)
- [UnlockAndRelock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlockandrelock#unlockandrelock)
- [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock)
