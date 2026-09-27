<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_softwareupdatesmanager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CancelDownload Method in Class CCM\_SoftwareUpdatesManager

The `CancelDownload` WMI class method, in Configuration Manager, cancels an in-progress download of software updates during a deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 CancelDownload();
```

#### Parameters

None.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

The `CancelDownload` method cancels the download only for deployments that are initiated by the Software Updates Client Agent or through the Configuration Manager SDK. If the software updates deployment was initiated as the result of a deadline, the call to this method fails.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[CCM\_SoftwareUpdatesManager Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwareupdatesmanager-client-wmi-class)
