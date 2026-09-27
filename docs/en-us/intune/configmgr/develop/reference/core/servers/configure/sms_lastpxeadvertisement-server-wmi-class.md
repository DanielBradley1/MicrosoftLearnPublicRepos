<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_lastpxeadvertisement-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_LastPXEAdvertisement Server WMI Class

The `SMS_LastPXEAdvertisement` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the last PXE advertisement.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_LastPXEAdvertisement : SMS_BaseClass
{
    String AdvertisementID;
    DateTime LastPXEAdvertisementTime;
    String NetbiosName;
    UInt32 ResourceId;
    String SMBIOSGUID;
};
```

## Methods

The `SMS_LastPXEAdvertisement` class does not define any methods.

## Properties

`AdvertisementID` Data type: `String`

Access type: Read/Write

Qualifiers: none

The advertisement ID.

`LastPXEAdvertisementTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The time of last PXE advertisement for this equipment.

`NetbiosName` Data type: `String`

Access type: Read/Write

Qualifiers: none

The NETBIOS name for the resource, which is often the same as the host name.

`ResourceId` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Key of the item.

`SMBIOSGUID` Data type: `String`

Access type: Read/Write

Qualifiers: none

The GUID of the BIOS.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
