<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedowloadprovider-interface -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICcmAlternateDownloadProvider Interface

The **ICcmAlternateDownloadProvider** interface, in Configuration Manager, defines the interface for an alternative download provider to be invoked by Content Transfer Manager to download packages.

## Syntax

```
[
    uuid(89F7454D-71F7-4F05-8276-FADC8B85F48D),
    object,
    pointer_default(unique)
]
```

## Methods

The **ICcmAlternateDownloadProvider** interface defines the following methods.

| Method | Description |
| --- | --- |
| [ICcmAlternatedownloadProvider : CancelJob Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---canceljob-method) | Cancels a job. |
| [ICcmAlternatedownloadProvider : DownloadContent Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---downloadcontent-method) | Instructs the provider to download content. |
| [ICcmAlternatedownloadProvider : ModifyJobSource Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobsource-method) | Instructs the provider to modify the source location for a given job. |
| [ICcmAlternatedownloadProvider : ModifyJobPriority Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobpriority-method) | Instructs the provider to modify the priority for a given job. |
| [ICcmAlternatedownloadProvider : ModifyJobTimeout Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---modifyjobtimeout-method) | Instructs the provider to modify the timeout for a given job. |
| [ICcmAlternatedownloadProvider : Resume Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---resume-method) | Instructs the provider to resume a given job. |
| [ICcmAlternatedownloadProvider : Suspend Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iccmalternatedownloadprovider---suspend-method) | Suspends a given job. |

## Remarks

ISVs should implement this interface and create an instance of local CCM\_DownloadProvider policy that corresponds to their implementation.

Important

This interface must be implemented out-of-process from ccmexec.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
