<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/wopi-requirements -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# WOPI implementation requirements for mobile integration

The following describes the implementation requirements for Microsoft 365 for mobile integration.

Note

This content applies to Microsoft 365 for mobile. Both of the endpoints require the same level of WOPI implementation.

This section documents specific requirements for your WOPI implementation for integration with Microsoft 365 for mobile beyond what's documented in general for WOPI. Learn more about how Microsoft 365 for mobile uses these operations in the [Operational flows for Microsoft 365 for mobile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/scenarios/operational-flows) section.

## Required WOPI Operations for Microsoft 365 for mobile

The following WOPI operations are required for integrating with Microsoft 365 for mobile. Operations not listed here aren't currently called by Microsoft 365 for mobile.

If some operations aren't supported for a specific user, file, or container, just be sure to return the correct values in [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) and [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo).

### File Operations

- [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo)
- [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile)
- [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock)
- [GetLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getlock#getlock)
- [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock)
- [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock)
- [UnlockAndRelock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlockandrelock#unlockandrelock)
- [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile)
- [EnumerateAncestors \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/enumerateancestors#enumerateancestors-files)

### Container Operations

- [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo)
- [CreateChildFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildfile#createchildfile)
- [EnumerateAncestors \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumerateancestors)
- [EnumerateChildren \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/enumeratechildren#enumeratechildren-containers)

### Ecosystem Operations

- [CheckEcosystem](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/checkecosystem)
- [GetRootContainer \(ecosystem\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/ecosystem/getrootcontainer#getrootcontainer-ecosystem)

### Bootstrapper

- [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap)
- [GetNewAccessToken](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getnewaccesstoken)
- [GetRootContainer \(bootstrapper\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/getrootcontainer#getrootcontainer-bootstrapper)

### Future Support

While these WOPI operations aren't currently used by Microsoft 365 for mobile, they must be implemented. Microsoft 365 for mobile might use these operations in the future.

- [RenameFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/renamefile)
- [DeleteFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/deletefile)
- [CreateChildContainer](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/createchildcontainer)
- [DeleteContainer](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/deletecontainer#deletecontainer)
- [RenameContainer](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/renamecontainer#renamecontainer)
- [GetEcosystem \(files\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getecosystem#getecosystem-files)
- [GetEcosystem \(containers\)](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/getecosystem#getecosystem-containers)

### Other Requirements

- The **X-WOPI-ItemVersion** header must be included on [PutFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/putfile), [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock), and [Unlock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlock) responses.
- For the [Bootstrap](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/bootstrapper/bootstrap) operation, the [Content-Type](https://tools.ietf.org/html/rfc7231#section-3.1.1.5) response header must be set to `application/json`.
- [IsEduUser](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#iseduuser) and [LicenseCheckForEditIsEnabled](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#licensecheckforeditisenabled) are required on [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) and [CheckContainerInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/containers/checkcontainerinfo). The values from CheckFileInfo must match that of the file’s parent container.
