<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_maintenancetask-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SCI\_MaintenanceTask Server WMI Class

The `SMS_SCI_MaintenanceTask` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a site control item maintenance task.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_MaintenanceTask : SMS_SiteControlItem
{
     String BackupLocation;
     DateTime BeginTime;
     UInt32 DaysOfWeek;
     Boolean Enabled;
     UInt32 FileType;
     String ItemName;
     String ItemType;
     DateTime LatestBeginTime;
     UInt32 NumRefreshDays;
     String SiteCode;
     String TaskName;
     UInt32 TaskType;
};
```

## Methods

The `SMS_SCI_MaintenanceTask` class does not define any methods.

## Properties

`BackupLocation` Data type: `String`

Access type: Read/Write

Qualifiers: None

The location of the backup for the maintenance task.

`BeginTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Beginning time for execution of the maintenance task. The default value is "00000000000000.000000+\*\*\*". Only the hours and minutes of this property are used.

`DaysOfWeek` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits\]

Days of the week on which the maintenance task executes. Possible values are listed below. The default value is SUNDAY \(0\).

| Value | Maintenance task day |
| --- | --- |
| 0 | SUNDAY |
| 1 | MONDAY |
| 2 | TUESDAY |
| 3 | WEDNESDAY |
| 4 | THURSDAY |
| 5 | FRIDAY |
| 6 | SATURDAY |

`Enabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if the maintenance task is activated.

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key, enumeration:ToSubClass\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`LatestBeginTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Latest beginning time of execution for the maintenance task. The default value is "00000000000000.000000+\*\*\*". Only the hours and minutes of this property are used.

`NumRefreshDays` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Number of days between maintenance task executions. The default value is 0.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: \[key, SizeLimit\("3"\)\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`TaskName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the maintenance task.

`TaskType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[enumeration\]

Type of maintenance task. Currently the only possible value is BACKUP \(1\).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class)
