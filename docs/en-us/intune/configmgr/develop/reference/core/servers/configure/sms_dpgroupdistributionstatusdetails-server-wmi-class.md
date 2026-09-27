<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupdistributionstatusdetails-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DPGroupDistributionStatusDetails Server WMI Class

The `SMS_DPGroupDistributionStatusDetails` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents distribution point status details.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DPGroupDistributionStatusDetails : SMS_BaseClass
{
    String ContentName;
    String DPName;
    String GroupID;
    UInt64 ID;
    String InsString1;
    String InsString10;
    String InsString2;
    String InsString3;
    String InsString4;
    String InsString5;
    String InsString6;
    String InsString7;
    String InsString8;
    String InsString9;
    UInt32 MessageCategory;
    UInt32 MessageFullID;
    UInt32 MessageID;
    UInt32 MessageSeverity;
    UInt32 MessageState;
    String ObjectID;
    UInt32 ObjectType;
    UInt32 ObjectTypeID;
    String PackageID;
    String SiteCode;
    UInt64 StatusMsgID;
    DateTime StatusTime;
};
```

## Methods

The `SMS_DPGroupDistributionStatusDetails` class does not define any methods.

## Properties

`ContentName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the package or application.

`DPName` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the distribution point.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Unique identifier for the distribution point group.

`ID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: \[key\]

Status message identifier.

`InsString1` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString10` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString2` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString3` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString4` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString5` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString6` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString7` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString8` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`InsString9` Data type: `String`

Access type: Read/Write

Qualifiers: none

Insertion string for the given status message.

`MessageCategory` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Status message category.

`MessageFullID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Status message full ID with severity.

`MessageID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Identifier for the status message.

`MessageSeverity` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

Severity of the status message.

| Value | Status message severity |
| --- | --- |
| 0x40000000 | Success |
| 0x80000000 | Warning |
| 0xC0000000 | Error |

`MessageState` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

State of the message.

| Value | Message state |
| --- | --- |
| 1 | Success |
| 2 | InProgress |
| 3 | Error |

`ObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Name of the package or application.

`ObjectType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[enumeration\]

Object type.

| Value | Object type |
| --- | --- |
| Value | Description |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 4 | PKG\_TYPE\_TASK\_SEQUENCE |
| 5 | PKG\_TYPE\_SWUPDATES |
| 6 | PKG\_TYPE\_DEVICE\_SETTING |
| 8 | PKG\_CONTENT\_PACKAGE |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |
| 512 | APPLICATION |

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

Secured object class ID.

| Value | Object type |
| --- | --- |
| Value | Description |
| 2 | SMS\_Package |
| 14 | SMS\_OperatingSystemInstallPackage |
| 18 | SMS\_ImagePackage |
| 19 | SMS\_BootImagePackage |
| 23 | SMS\_DriverPackage |
| 24 | SMS\_SoftwareUpdatesPackage |
| 31 | SMS\_Application |

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: none

Identifier for the package.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: none

Source site for this status.

`StatusMsgID` Data type: `UInt64`

Access type: Read/Write

Qualifiers: none

Status message instance identifier.

`StatusTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

See [SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
