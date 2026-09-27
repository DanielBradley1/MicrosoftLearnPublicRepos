<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/readfromstring-method-in-class-sms_schedulemethods -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ReadFromString Method in Class SMS\_ScheduleMethods

The `ReadFromString` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, reads [SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class) objects from an interval string.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ReadFromString(
   String StringData,
     SMS_ScheduleToken TokenData[]
);
```

#### Parameters

`StringData` Data type: `String`

Qualifiers: \[in\]

The interval string \(details in table below\).

`TokenData` Data type: `SMS_ScheduleToken` Array

Qualifiers: \[out\]

[SMS\_ScheduleToken Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scheduletoken-server-wmi-class) objects.

```

The ScheduleToken class uses two DWORDs to store the schedule data.

Values for the first DWORD laid out as follows:

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +-----------+---------+---------+-------+-----------+-----------+
 |  Start    |  Start  |  Start  | Start |   Start   | Duration  |
 |  Minute   |  Hour   |  Day    | Month |   Year    | Minutes   |
 +-----------+---------+---------+-------+-----------+-----------+

Values for the second DWORD laid out as follows:

 SCHED_TOKEN_RECUR_NONE

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +---------+---------+-----+-------------------------------------+
 | Duration| Duration|Flags|           Unused                  |U|
 | Hours   | Days    |     |                                   |T|
 |         |         |     |                                   |C|
 +---------+---------+-----+-------------------------------------+

 SCHED_TOKEN_RECUR_INTERVAL

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +---------+---------+-----+-----------+---------+---------+-----+
 | Duration| Duration|Flags|  Num of   |  Num of |  Num of |   |U|
 | Hours   | Days    |     |  Minutes  |  Hours  |  Days   |   |T|
 |         |         |     |           |         |         |   |C|
 +---------+---------+-----+-------------------------------------+

 SCHED_TOKEN_RECUR_WEEKLY

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +---------+---------+-----+-----+-----+-------------------------+
 | Duration| Duration|Flags| Week|# of |       Unused          |U|
 | Hours   | Days    |     | Day |Weeks|                       |T|
 |         |         |     |     |     |                       |C|
 +---------+---------+-----+-------------------------------------+

 SCHED_TOKEN_RECUR_MONTHLY_BY_WEEKDAY

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +---------+---------+-----+-----+-------+-----+-----------------+
 | Duration| Duration|Flags| Week|Num of |Week |     Unused    |U|
 | Hours   | Days    |     | Day |months |Order|               |T|
 |         |         |     |     |       |     |               |C|
 +---------+---------+-----+-------------------------------------+

 SCHED_TOKEN_RECUR_MONTHLY_BY_DATE

  3 3 2 2 2 2 2 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1
  1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0 9 8 7 6 5 4 3 2 1 0
 +---------+---------+-----+---------+-------+-------------------+
 | Duration| Duration|Flags|   Date  |Num of |       Unused    |U|
 | Hours   | Days    |     |         |months |                 |T|
 |         |         |     |         |       |                 |C|
 +---------+---------+-----+-------------------------------------+
```

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ScheduleMethods Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_schedulemethods-server-wmi-class) [WriteToString Method in Class SMS\_ScheduleMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/writetostring-method-in-class-sms_schedulemethods)
