<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_st_recurweekly-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ST\_RecurWeekly Server WMI Class

The `SMS_ST_RecurWeekly` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a schedule token for events that occur at weekly intervals, for example, every third week on Wednesday.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ST_RecurWeekly : SMS_ScheduleToken
{
      UInt32 Day;
      UInt32 DayDuration;
      UInt32 ForNumberOfWeeks;
      UInt32 HourDuration;
      Boolean IsGMT;
      UInt32 MinuteDuration;
      DateTime StartTime;
};
```

## Methods

The `SMS_ST_RecurWeekly` class does not define any methods.

## Properties

`Day` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Day of the week when the event is scheduled to occur. Possible values are listed below. The default value is 1.

| Value | Day |
| --- | --- |
| 1 | SUNDAY |
| 2 | MONDAY |
| 3 | TUESDAY |
| 4 | WEDNESDAY |
| 5 | THURSDAY |
| 6 | FRIDAY |
| 7 | SATURDAY |

`DayDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Range\("0-31"\)\]

See [SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class).

`ForNumberOfWeeks` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Range\("1-4"\)\]

Number of weeks for recurrence. Allowable values are in the range 1-4. The default value is 1.

`HourDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Range\("0-23"\)\]

See [SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class).

`IsGMT` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class).

`MinuteDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Range\("0-59"\)\]

See [SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class).

`StartTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

See [SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class)
