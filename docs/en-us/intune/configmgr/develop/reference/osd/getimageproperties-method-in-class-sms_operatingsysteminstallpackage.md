<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getimageproperties-method-in-class-sms_operatingsysteminstallpackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetImageProperties Method in Class SMS\_OperatingSystemInstallPackage

The `GetImageProperties` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, reads all metadata from the specified .wim source file to an XML string.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetImageProperties(
      String SourceImagePath,
      String ImageProperty
);
```

#### Parameters

`SourceImagePath` Data type: `String`

Qualifiers: \[in\]

The path to the source file to query for metadata.

`ImageProperty` Data type: `String`

Qualifiers: \[out\]

The XML string defining the metadata.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

This method accesses the source .wim file metadata by using the `ImageProperty` property of [SMS\_OperatingSystemInstallPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_operatingsysteminstallpackage-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_OperatingSystemInstallPackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_operatingsysteminstallpackage-server-wmi-class) [ReloadImageProperties Method in Class SMS\_OperatingSystemInstallPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_operatingsysteminstallpackage)
