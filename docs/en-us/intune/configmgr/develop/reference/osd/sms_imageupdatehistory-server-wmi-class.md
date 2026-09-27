<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imageupdatehistory-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ImageUpdateHistory Server WMI Class

The `SMS_ImageUpdateHistory` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents software update installation history of offline servicing image.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageUpdateHistory : SMS_BaseClass
{
    SInt32 FailedUpdateID;
    String ImagePackageID;
    DateTime RunDateTime;
    SInt32 ScheduleID;
    SInt32 Status;
};
```

## Methods

The `SMS_ImageUpdateHistory` class does not define any methods.

## Properties

`FailedUpdateID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

ID for software update that failed to install.

`ImagePackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

ID for offline servicing image.

`RunDateTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: \[key\]

Last run time for software update.

`ScheduleID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key\]

ID for software update installation schedule.

`Status` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

Software update installation status.

| Value | Installation status |
| --- | --- |
| 2 | Success |
| 3 | Failed |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
