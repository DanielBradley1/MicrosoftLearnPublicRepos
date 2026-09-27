<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_lastsoftwarescan-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_System\_LastSoftwareScan Server WMI Class

The `SMS_G_System_LastSoftwareScan` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents information about the most recent software inventory scan on the client computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_LastSoftwareScan : SMS_G_System
{
     UInt32 ResourceID;
     DateTime LastScanDate;
     UInt32 LastScanOpcode;
     DateTime LastCollectedFileScanDate;
};
```

## Methods

The `SMS_G_System_LastSoftwareScan` class does not define any methods.

## Properties

`ResourceID` Data type: **UInt32**

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_G\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class).

`LastCollectedFileScanDate` Data type: **DateTime**

Access type: Read/Write

Qualifiers: None

The date and time of the last scan for collected files.

`LastScanDate` Data type: **DateTime**

Access type: Read/Write

Qualifiers: None

Date and time of the most recent Configuration Manager software inventory scan.

`LastScanOpcode` Data type: **UInt32**

Access type: Read/Write

Qualifiers: None

Not used.

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_G\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class)
