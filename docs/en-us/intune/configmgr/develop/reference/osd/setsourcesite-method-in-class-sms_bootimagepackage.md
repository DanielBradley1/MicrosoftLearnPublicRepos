<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsourcesite-method-in-class-sms_bootimagepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetSourceSite Method in Class SMS\_BootImagePackage

The `SetSourceSite` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, sets the code of the source site for the boot image package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 SetSourceSite(
      String SourceSite
);
```

#### Parameters

`SourceSite` Data type: `String`

Qualifiers: \[in\]

The code of the source site for the boot image package.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class)
