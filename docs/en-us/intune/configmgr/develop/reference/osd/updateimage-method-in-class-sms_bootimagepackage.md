<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/updateimage-method-in-class-sms_bootimagepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# UpdateImage Method in Class SMS\_BootImagePackage

The `UpdateImage` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, creates a copy of the current boot image source .wim file and updates the copy with the most current operating system deployment binaries.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 UpdateImage();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

Your application calls this method only when Configuration Manager is upgrading from an operating system release candidate to an RTM version.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class)
