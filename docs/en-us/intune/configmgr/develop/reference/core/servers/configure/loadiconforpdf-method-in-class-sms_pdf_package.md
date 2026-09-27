<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/loadiconforpdf-method-in-class-sms_pdf_package -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# LoadIconForPDF Method in Class SMS\_PDF\_Package

The `LoadIconForPDF` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, imports a required icon for a package definition file.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 LoadIconForPDF(
    UInt32 PDFID,
     String IconFileName,
     UInt8 Icon[]
);
```

#### Parameters

`PDFID` Data type: `UInt32`

Qualifiers: \[in\]

ID of the package definition file to which to add icons. Get this value from the `PDFID` parameter of the [LoadPDF Method in Class SMS\_PDF\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/loadpdf-method-in-class-sms_pdf_package) method.

`IconFileName` Data type: `String`

Qualifiers: \[in, SizeLimit\("100"\)\]

Full path and file name of a required package definition file icon. Get the icon name from the `RequriedIconNames` parameter of the `LoadPDF` method. Include the path if necessary.

`Icon` Data type: `UInt8` Array

Qualifiers: \[in\]

Icon to associate with the package.

## Return Values

An `SInt32` data type.

## Remarks

Package definition files can reference icons to be used with the package. These icons are not part of the file and must be loaded separately.

Your application must call `LoadIconForPDF` for every icon that [LoadPDF Method in Class SMS\_PDF\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/loadpdf-method-in-class-sms_pdf_package) loads.

## Example Code

For an example that uses the `LoadIconForPDF` method, see [LoadPDF Method in Class SMS\_PDF\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/loadpdf-method-in-class-sms_pdf_package).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_PDF\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class)
