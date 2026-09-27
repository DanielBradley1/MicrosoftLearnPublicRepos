<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/installupdates-method-in-class-ccm_softwareupdatesmanager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# InstallUpdates Method in Class CCM\_SoftwareUpdatesManager

The `InstallUpdates` WMI class method, in Configuration Manager, installs software updates that have been deployed to the client computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 InstallUpdates(
     [IN]  CCM_SoftwareUpdate CCMUpdates[]
);
```

#### Parameters

`CCMUpdates[]` Data type: `CCM_SoftwareUpdate`

Qualifiers: \[in\]

Array of software updates that are installed.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[CCM\_SoftwareUpdatesManager Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwareupdatesmanager-client-wmi-class)
