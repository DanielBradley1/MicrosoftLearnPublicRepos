<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/console/sms_roleinobjecttype-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# SMS\_RoleInObjectType Server WMI Class

The `SMS_RoleInObjectType` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager that maps a role and its associated object types.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_RoleInObjectType : SMS_BaseClass
{
    UInt32 ObjectTypeID;
    String RoleID;
};
```

## Methods

The `SMS_RoleInObjectType` class doesn't define any methods.

## Properties

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Secured object class ID. Possible values are listed below.

| Value | Object type ID |
| --- | --- |
| 2 | SMS\_Package |
| 14 | SMS\_OperatingSystemInstallPackage |
| 18 | SMS\_ImagePackage |
| 19 | SMS\_BootImagePackage |
| 21 | SMS\_DeviceSettingPackage |
| 23 | SMS\_DriverPackage |
| 24 | SMS\_SoftwareUpdatesPackage |
| 31 | SMS\_Application |

`RoleID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

The ID of the role.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
