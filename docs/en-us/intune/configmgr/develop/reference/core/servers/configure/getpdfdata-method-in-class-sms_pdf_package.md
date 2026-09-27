<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getpdfdata-method-in-class-sms_pdf_package -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetPDFData Method in Class SMS\_PDF\_Package

The `GetPDFData` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, produces [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) and [SMS\_Program Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_program-server-wmi-class) objects from a loaded package definition file.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetPDFData(
     UInt32 PDFID,
     SMS_Package PackageData,
      SMS_Program ProgramData[]
);
```

#### Parameters

`PDFID` Data type: `UInt32`

Qualifiers: \[in\]

ID of the package definition file to be retrieved. Get this value from the [SMS\_PDF\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class) class.

`PackageData` Data type: `SMS_Package`

Qualifiers: \[out\]

An [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) object produced from the package definition file.

`ProgramData` Data type: `SMS_Program` Array

Qualifiers: \[out\]

[SMS\_Program Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_program-server-wmi-class) objects produced from the package definition file.

## Return Values

An `SInt32` data type that is one of the following bit-field warning flags.

| Flag | Description |
| --- | --- |
| WARN\_BAD\_RUN \(0\) | Invalid run information specified. |
| WARN\_BAD\_RESTART \(1\) | Invalid restart information specified. |
| WARN\_BAD\_CANRUNWHEN \(2\) | Invalid CanRunWhen information specified. |
| WARN\_BAD\_ASSIGNMENT \(3\) | Invalid assignment information specified. |
| WARN\_BAD\_DEPENDPROG \(4\) | Invalid DependentProgram information specified. |
| WARN\_BAD\_SPECIFYDRIVE \(5\) | Invalid SpecifyDrive information specified. |
| WARN\_BAD\_ESTDISKSPACE \(6\) | Invalid EstimatedDiskSpace information specified. |
| WARN\_NO\_SUPPCLINFO \(7\) | No SupportedClients information specified. |
| WARN\_BAD\_SUPPCLINFO \(8\) | Invalid SupportedClients information specified. |
| WARN\_VER1PDF \(9\) | Version 1.0 file used. |
| WARN\_REMPRONOUKEY\(10\) | The remove program is set, but no uninstall Key is given. |

## Example Code

For an example that uses this method, see [How to Create a Package Using a PDF Template](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-package-by-using-a-package-definition-file-template).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_PDF\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pdf_package-server-wmi-class)
