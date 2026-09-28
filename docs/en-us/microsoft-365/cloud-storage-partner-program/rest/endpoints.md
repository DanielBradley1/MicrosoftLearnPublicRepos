<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/endpoints -->
<!-- Sitemap-Last-Modified: 2022-06-02 -->

# WOPI REST endpoints

A WOPI host needs to provide some information about the files it stores, as well as the binary contents of those files. Because WOPI is a REST-based callback interface, this information is provided via specific URLs. A WOPI host provides a small REST API around its files. WOPI clients such as Microsoft 365 for the web then use those REST API to work with the files.

Not all operations and endpoints are required. All actions require the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) and [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile) operations.

Each WOPI endpoint supports a number of operations specified by the caller in the **X-WOPI-Override** request header. Parameters for each operation are also passed in HTTP headers, which all begin with `X-WOPI-`. This way, executing a WOPI operation is as simple as issuing a request to the appropriate REST endpoint and passing appropriate HTTP header values with the request.

Note

[Standard WOPI request and response headers](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/common-headers)

## Endpoint URLs

All WOPI host endpoints must be located at a URL that *starts* with `/wopi`. For example, all of the following URLs are **valid** URLs for the [File contents endpoint](#file-contents-endpoint) for a file with the ID `abc123`:

- `https://api.contoso.com/modules/wopi/files/abc123/contents`
- `https://test.wopi.contoso.com/wopi_test/files/abc123/contents`

However, the following URLs are **not valid**:

- `https://api.contoso.com/api_wopi/files/abc123/contents` \(invalid because the endpoint URL does not *start* with `/wopi`\)
- `https://api.contoso.com/files/abc123/contents` \(invalid because the endpoint URL does not *start* with `/wopi`\)
- `https://test.wopi.contoso.com/officeonline/files/abc123/contents` \(invalid because the endpoint URL does not *start* with `/wopi`\)
- `https://wopi.contoso.com/wopi/files/ids/abc123/contents` \(invalid because the endpoint URL contains `/ids`, which is not permitted\)

## Files endpoint

The Files endpoint provides access to file-level operations.

### URL

`/wopi/files/(file_id)`

The following operations are exposed through this endpoint:

- [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo)
- [PutRelativeFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putrelativefile)
- [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock)
- [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock)
- [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock)
- [UnlockAndRelock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlockandrelock#unlockandrelock)
- [DeleteFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/deletefile)
- [RenameFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile)

## File contents endpoint

The File contents endpoint provides access to retrieve and update the contents of a file.

### URL

`/wopi/files/(file_id)/contents`

The following operations are exposed through this endpoint:

- [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile)
- [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile)

## Containers endpoint

### URL

`/wopi/containers/(container_id)`

The following operations are exposed through this endpoint:

- [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo)
- [CreateChildContainer](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildcontainer)
- [CreateChildFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildfile#createchildfile)
- [DeleteContainer](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/deletecontainer)
- [EnumerateAncestors \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumerateancestors)
- [EnumerateChildren \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumeratechildren)
- [RenameContainer](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/renamecontainer#renamecontainer)

## Ecosystem endpoint

The Ecosystem endpoint serves as a bridge for WOPI clients that do not have a File or Container ID that they are operating on.

### URL

`/wopi/ecosystem`

The following operations are exposed through this endpoint:

- [CheckEcosystem](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/checkecosystem)
- [🚧 GetFileWopiSrc \(ecosystem\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getfilewopisrc)
- [GetRootContainer \(ecosystem\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getrootcontainer)

## Bootstrapper endpoint

The following operations are exposed through this endpoint:

- [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap)
- [GetNewAccessToken](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getnewaccesstoken)
- [Shortcut operations](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/shortcuts#shortcut-operations)
