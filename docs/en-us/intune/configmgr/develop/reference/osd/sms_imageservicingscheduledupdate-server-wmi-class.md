<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imageservicingscheduledupdate-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ImageServicingScheduledUpdate Server WMI Class

The `SMS_ImageServicingScheduledUpdate` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents all schedules for one software update in offline servicing image.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ImageServicingScheduledUpdate : SMS_BaseClass
{
    SInt32 ScheduleID;
    SInt32 UpdateID;
};
```

## Methods

The `SMS_ImageServicingScheduledUpdate` class does not define any methods.

## Properties

`ScheduleID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key\]

ID for software update installation schedule.

`UpdateID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key\]

ID for software update in offline servicing image.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
