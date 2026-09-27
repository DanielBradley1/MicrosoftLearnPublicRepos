<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imageservicingprogress-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ImageServicingProgress Server WMI Class

The `SMS_ImageServicingProgress` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents software update installation status in offline servicing image.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageServicingProgress : SMS_BaseClass
{
    SInt32 FailedUpdateID;
    String ImagePackageID;
    DateTime RunDateTime;
    SInt32 ScheduleID;
    SInt32 Status;
    SInt32 Win32ErrorCode;
};
```

## Methods

The `SMS_ImageServicingProgress` class does not define any methods.

## Properties

`FailedUpdateID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Failed software update local unique ID.

`ImagePackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Package ID of the image applied to the target computer.

`RunDateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last run time of software update.

`ScheduleID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key\]

Schedule ID for software update installation.

`Status` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Status for software update installation.

| Value | Installation status |
| --- | --- |
| 1 | Running |
| 2 | Success |
| 3 | Failed |

`Win32ErrorCode` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Win32 error code for software update installation.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
