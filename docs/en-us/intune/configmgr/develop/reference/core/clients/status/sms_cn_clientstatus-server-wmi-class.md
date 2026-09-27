<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/status/sms_cn_clientstatus-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CN\_ClientStatus Server WMI Class

The `SMS_CN_ClientStatus` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents client notification of agent status.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CN_ClientStatus : SMS_BaseClass
{
    UInt32 ChannelType;
    DateTime LastStatusTime;
    UInt32 OnlineStatus;
    UInt32 ResourceID;
    UInt32 ServerID;
};
```

## Methods

The following table lists the methods in the `SMS_CN_ClientStatus` class.

| Method | Description |
| --- | --- |
| [GetOnlineCount Method in Class SMS\_CN\_ClientStatus](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/status/getonlinecount-method-in-class-sms_cn_clientstatus) | Gets an online count of the selected clients of the target collection. |

## Properties

`ChannelType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Channel type. Possible values are:

| Value | Channel type |
| --- | --- |
| 0 | TCP |
| 1 | HTTP |

`LastStatusTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Last online time.

`OnlineStatus` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Online status. Possible values are:

| Value | Online status |
| --- | --- |
| 0 | Offline |
| 1 | Online |

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Client resource identifier.

`ServerID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Client notification server identifier.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
