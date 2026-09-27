<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_st_recurinterval-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ST\_RecurInterval Server WMI Class

The `SMS_ST_RecurInterval` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a schedule token for events that occur at regular intervals, for example, every 10 days.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ST_RecurInterval : SMS_ScheduleToken
{
      UInt32 DayDuration;
      UInt32 DaySpan;
      UInt32 HourDuration;
      UInt32 HourSpan;
      Boolean IsGMT;
      UInt32 MinuteDuration;
      UInt32 MinuteSpan;
      DateTime StartTime;
};
```

## Methods

The `SMS_ST_RecurInterval` class does not define any methods.

## Properties

`DayDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class).

`DaySpan` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Range\("0-31"\)\]

Number of days spanning schedule intervals. Allowable values are in the range 0-31. The default value is 0.

`HourDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Range\("0-23"\)\]

See [SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class).

`HourSpan` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Range\("0-23"\)\]

Number of hours spanning schedule intervals. Allowable values are in the range 0-23. The default value is 0.

`IsGMT` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class).

`MinuteDuration` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Range\("0-59"\)\]

See [SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class).

`MinuteSpan` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[Range\("0-59"\)\]

Number of minutes spanning schedule intervals. Allowable values are in the range 0-59. The default value is 0.

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
