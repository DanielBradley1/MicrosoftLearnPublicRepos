<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupdistributionstatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DPGroupDistributionStatus Server WMI Class

The `SMS_DPGroupDistributionStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that describes distribution information for a given distribution point group.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DPGroupDistributionStatus : SMS_BaseClass
{
    UInt32 Assets;
    UInt32 ContentCount;
    String GroupID;
    UInt32 MessageCategory;
    UInt32 MessageType;
    DateTime StatusTime;
};
```

## Methods

The `SMS_DPGroupDistributionStatus` class doesn't define any methods.

## Properties

`Assets` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Count of distribution points.

`ContentCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Count of packages or applications distributed to this distribution point group.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Unique identifier for the distribution point group.

`MessageCategory` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Status message category.

`MessageType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

See [SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class).

`StatusTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

Date and time, in Universal Coordinated Time \(UTC\), when the status message was created.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
