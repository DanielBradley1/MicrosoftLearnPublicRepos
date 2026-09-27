<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/iscurrentworkingupdatepackage-method-in-class-sms_cm_updatepackages -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IsCurrentWorkingUpdatePackage Method in Class SMS\_CM\_UpdatePackages

The `IsCurrentWorkingUpdatePackage` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, checks whether the update package is the package that setup is currently working on.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 IsCurrentWorkingUpdatePackage(
     boolean IsCurrentWorkingUpdatePackage
);
```

#### Parameters

`IsCurrentWorkingUpdatePackage` Data type: `Boolean`

Qualifiers: \[out\]

`true` if the update package is the package that setup is currently working on; otherwise, `false`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_CM\_UpdatePackages Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackages-server-wmi-class)
