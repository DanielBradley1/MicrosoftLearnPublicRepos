<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/exportdefaultbootimage-method-in-class-sms_bootimagepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ExportDefaultBootImage Method in Class SMS\_BootImagePackage

The `ExportDefaultBootImage` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, finalizes a boot image and then exports the image from the specified source to the specified location.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ExportDefaultBootImage(
     String Architecture,
     UInt32 ImageIndex,
     String ExportImagePath
);
```

#### Parameters

`Architecture` Data type: `String`

Qualifiers: \[in\]

Operating system architecture of the boot image. Possible values are:

| Value | Architecture |
| --- | --- |
| x86 | I386 32-bit microprocessor |
| ia64 | Itanium 64-bit microprocessor |
| x64 | X86-64 64-bit microprocessor |

`ImageIndex` Data type: `UInt32`

Qualifiers: \[in\]

The index of the boot image in the Windows Assessment and Deployment Kit source that is used by Configuration Manager setup.

`ExportImagePath` Data type: `String`

Qualifiers: \[in\]

The destination path of the boot image to export, for example, c:\\winPE\\boot.wim.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

Note

Because Configuration Manager uses this method in importing the operating system, be sure to use secure programming techniques in your application or script.

The `ExportDefaultBootImage` method is not thread-safe.

This method finalizes a boot image by adding components or deleting old components to reduce the image size. Each .wim file can contain multiple images, but the export occurs only for the boot image.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class)
