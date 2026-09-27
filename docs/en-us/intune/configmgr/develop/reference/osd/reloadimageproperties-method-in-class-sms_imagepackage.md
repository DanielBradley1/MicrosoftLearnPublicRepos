<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_imagepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ReloadImageProperties Method in Class SMS\_ImagePackage

The `ReloadImageProperties` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, reloads image metadata from an image source .wim file and synchronizes the metadata with the database.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ReloadImageProperties();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

For an example of the use of this method, see [How to Update an Operating System Image Package in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-update-an-operating-system-image-package).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imagepackage-server-wmi-class) [GetImageProperties Method in Class SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getimageproperties-method-in-class-sms_imagepackage) [How to Update an Operating System Image Package in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-update-an-operating-system-image-package)
