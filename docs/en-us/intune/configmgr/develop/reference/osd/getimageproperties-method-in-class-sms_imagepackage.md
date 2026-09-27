<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getimageproperties-method-in-class-sms_imagepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetImageProperties Method in Class SMS\_ImagePackage

The `GetImageProperties` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, reads all metadata from the specified .wim source file for an image to an XML string.

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

Path to the .wim source file to query for metadata, for example, \\\\server\\share\\boot.wim.

`ImageProperty` Data type: `String`

Qualifiers: \[out\]

XML document containing the image metadata.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

This method accesses the source .wim file metadata by using the `ImageProperty` property of [SMS\_ImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imagepackage-server-wmi-class). For more information, see [How to View the Properties for an Operating System Image](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-view-the-properties-for-an-operating-system-image).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imagepackage-server-wmi-class) [ReloadImageProperties Method in Class SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_imagepackage)
