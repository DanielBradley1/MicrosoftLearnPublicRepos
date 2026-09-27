<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imageservicingscheduledimage-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ImageServicingScheduledImage Server WMI Class

The `SMS_ImageServicingScheduledImage` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents all schedules for offline servicing image.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageServicingScheduledImage : SMS_BaseClass
{
    String ImagePackageID;
    SInt32 ScheduleID;
};
```

## Methods

The `SMS_ImageServicingScheduledImage` class does not define any methods.

## Properties

`ImagePackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

ID for offline servicing image that is installed on client computer.

`ScheduleID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key\]

ID for offline servicing image installation schedule.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
