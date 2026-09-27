<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/updatedefaultimage-method-in-class-sms_bootimagepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# UpdateDefaultImage Method in Class SMS\_BootImagePackage

The `UpdateDefaultImage` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, creates a copy of the .wim image pointed to by the `ImagePath` property and injects it with operating system deployment files for boot image deployment.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 UpdateDefaultImage();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

This method expects an `SMS_BootImagePackage` instance with the `ImagePath` property being a valid .wim image.

Your application calls this method only when Configuration Manager is upgrading from an operating system release candidate to an RTM version.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class)
