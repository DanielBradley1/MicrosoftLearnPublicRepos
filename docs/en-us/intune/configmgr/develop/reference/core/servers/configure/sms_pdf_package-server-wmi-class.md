<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_PDF\_Package Server WMI Class

The `SMS_PDF_Package` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a package definition file \(PDF\) template from which to create an initialized package.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_PDF_Package : SMS_BaseClass
{
      UInt8 Icon[];
      UInt32 IconSize;
      String Language;
      String Name;
      String PDFFileName;
      UInt32 PDFID;
      String Publisher;
    String RequiredIconNames[];
      UInt32 Status;
      String Version;
};
```

## Methods

The following table lists the methods in the `SMS_PDF_Package` class.

| Method | Description |
| --- | --- |
| [GetPDFData Method in Class SMS\_PDF\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getpdfdata-method-in-class-sms_pdf_package) | Gets `SMS_Package` and `SMS_Program` objects for a loaded package definition file. |
| [LoadIconForPDF Method in Class SMS\_PDF\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/loadiconforpdf-method-in-class-sms_pdf_package) | Imports a required icon for a package definition file. |
| [LoadPDF Method in Class SMS\_PDF\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/loadpdf-method-in-class-sms_pdf_package) | Imports a package definition file into the package definition file store. |
| [ProcessInBox Method in Class SMS\_PDF\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/processinbox-method-in-class-sms_pdf_package) | Imports package definition files from the package definition file inbox. |

## Properties

`Icon` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: \[lazy, large\]

Icon to associate with the package in the Configuration Manager console.

`IconSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[lazy\]

Size, in bytes, of the icon. The default value is 0.

`Language` Data type: `String`

Access type: Read/Write

Qualifiers: None

Language for the package, for example, English.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the package.

`PDFFileName` Data type: `String`

Access type: Read/Write

Qualifiers: \[SizeLimit\("100"\)\]

File name of the package definition file. The file name does not include the .sms file name extension.

`PDFID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Unique auto-generated ID for the package definition file.

`Publisher` Data type: `String`

Access type: Read/Write

Qualifiers: None

Manufacturer of the package.

`RequiredIconNames` Data type: `String` Array

Access type: Read/Write

Qualifiers: \[lazy\]

Icons still required to be loaded.

`Status` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[lazy, Enumeration\]

Load status of the package definition file. Possible values are:

| Value | Load status |
| --- | --- |
| 0 | Loaded |
| 1 | RequiresIcon |

`Version` Data type: `String`

Access type: Read/Write

Qualifiers: None

Version number of the package.

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  This class contains methods that store the package definition file template in the package definition file store and that produce [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) objects and [SMS\_Program Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_program-server-wmi-class) objects from the template.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) [SMS\_Program Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_program-server-wmi-class)
