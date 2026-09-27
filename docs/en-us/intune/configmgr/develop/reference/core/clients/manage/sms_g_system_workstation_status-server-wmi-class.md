<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_workstation_status-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_System\_WORKSTATION\_STATUS Server WMI Class

The `SMS_G_System_WORKSTATION_STATUS` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that contains information about the last time inventory was collected on a client computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_WORKSTATION_STATUS : SMS_G_System_Current
{
     UInt32 GroupID;
     DateTime LastHardwareScan;
     String LastReportVersion;
     UInt32 ResourceID;
     UInt32 RevisionID;
     UInt32 SystemDefaultLocaleID;
     DateTime TimeStamp;
     UInt32 TimeZoneOffset
};
```

## Methods

The `SMS_G_System_WORKSTATION_STATUS` class does not define any methods.

## Properties

`GroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_G\_System\_Current Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class).

For this class, the default value of this property is NULL.

`LastHardwareScan` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when Configuration Manager inventoried the client computer hardware.

`LastReportVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

Version of the last report.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_G\_System\_Current Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class).

For this class, the default value of this property is `null`.

`RevisionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_G\_System\_Current Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class).

For this class, the default value of this property is `null`.

`SystemDefaultLocaleID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

System default locale ID.

`TimeStamp` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

See [SMS\_G\_System\_Current Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class).

For this class, the default value of this property is `null`.

`TimeZoneOffset` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

System default time zone offset.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## See Also

[Hardware Inventory Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/hardware-inventory-server-wmi-classes) [SMS\_G\_System\_Current Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_current-server-wmi-class)
