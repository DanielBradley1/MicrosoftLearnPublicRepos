<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/rebuildpackage-method-in-class-sms_softwareupdatespackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RebuildPackage Method in Class SMS\_SoftwareUpdatesPackage

The `RebuildPackage` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, brings the software updates package to its expected state if files are found to be corrupt or have been deleted.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 RebuildPackage(
     String ContentSourcePath
);
```

#### Parameters

`ContentSourcePath` Data type: `String`

Qualifiers: \[in, optional\]

Source path where the content files are located.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SoftwareUpdatesPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatespackage-server-wmi-class) [AddUpdateContent Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage) [RemoveContent Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/removecontent-method-in-class-sms_softwareupdatespackage)
