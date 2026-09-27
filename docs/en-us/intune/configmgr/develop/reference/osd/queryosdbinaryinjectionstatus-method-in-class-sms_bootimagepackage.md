<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/queryosdbinaryinjectionstatus-method-in-class-sms_bootimagepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# QueryOSDBinaryInjectionStatus Method in Class SMS\_BootImagePackage

The `QueryOSDBinaryInjectionStatus` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, queries the current status of the injection of operating system deployment binaries into a boot image.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 QueryOSDBinaryInjectionStatus(
     String ContextID,
     UInt32 Status,
     UInt32 Progress,
     UInt32 MaxProgress,
     String ProgressText,
     SInt32 ErrorCode,
     String ExtendedErrorInfo
);
```

#### Parameters

`ContextID` Data type: `String`

Qualifiers: \[in\]

The ID of the context \(index\) optionally associated with the status upon import of a boot image. This ID is indicated by the `ContextID` property of [SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class).

`Status` Data type: `UInt32`

Qualifiers: \[out\]

The current status of binary injection. Possible values are:

| Value | Status |
| --- | --- |
| 0 | Complete |
| 1 | In progress |
| 2 | Error |
| 3 | No status |

`Progress` Data type: `UInt32`

Qualifiers: \[out\]

The progress status indicating the number of the current step in the binary injection operation.

`MaxProgress` Data type: `UInt32`

Qualifiers: \[out\]

The total number of steps in the binary injection operation.

`ProgressText` Data type: `String`

Qualifiers: \[out\]

A user-readable string identifying the current progress of the binary injection operation.

`ErrorCode` Data type: `SInt32`

Qualifiers: \[out\]

A 32-bit error code in case of an error in the binary injection operation. An example of an error code is FILE\_NOT\_FOUND \(2\). The log file contains error code details.

`ExtendedErrorInfo` Data type: `String`

Qualifiers: \[out\]

Additional error information if the `ErrorCode` parameter is set to an error code. Currently this parameter is used to report driver file information if the binary injection operation fails to inject the binaries for a particular driver.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

To use the `QueryOSDBinaryInjectionStatus` method, your application must:

1. Establish a connection to the SMS Provider. For more information see, [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Access the [SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class) object.
3. Call the [ExportDefaultBootImage Method in Class SMS\_BootImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/exportdefaultbootimage-method-in-class-sms_bootimagepackage).
4. Then call `QueryOSDBinaryInjectionStatus` as needed to find out the status of the binary injection operation.
5. Use the values of the `Progress` and `MaxProgress` parameters to determine the percent complete status of the binary injection operation.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class) [ExportDefaultBootImage Method in Class SMS\_BootImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/exportdefaultbootimage-method-in-class-sms_bootimagepackage)
