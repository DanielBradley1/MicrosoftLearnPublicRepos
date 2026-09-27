<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdfpkgtopdfprogram_a-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_PDFPkgToPDFProgram\_a Server WMI Class

The `SMS_PDFPkgToPDFProgram_a` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that uses the `PDFID` property to relate a [SMS\_PDF\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class) object to an [SMS\_PDF\_Program Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_program-server-wmi-class) object that is part of the package.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_PDFPkgToPDFProgram_a : SMS_BaseAssociation
{
      ref:SMS_PDF_Package PDF_Package;
      ref:SMS_PDF_Program PDF_Program;
};
```

## Methods

The `SMS_PDFPkgToPDFProgram_a` class does not define any methods.

## Properties

`PDF_Package` Data type: `ref:SMS_PDF_Package`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_PDF\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class) object path.

`PDF_Program` Data type: `ref:SMS_PDF_Program`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_PDF\_Program Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_program-server-wmi-class) object path.

## Remarks

Class qualifiers for this class include:

- Association: ToInstance
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_PDF\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class) [SMS\_PDF\_Program Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_program-server-wmi-class)
