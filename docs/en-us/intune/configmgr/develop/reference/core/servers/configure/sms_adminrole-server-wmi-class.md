<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_adminrole-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_AdminRole Server WMI Class

The `SMS_AdminRole` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the association between the admin account and the security role.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_AdminRole : SMS_BaseClass
{
    UInt32 AdminID;
    String RoleID;
};
```

## Methods

The `SMS_AdminRole` class does not define any methods.

## Properties

`AdminID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

ID of the admin account.

`RoleID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

ID of the security role.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
