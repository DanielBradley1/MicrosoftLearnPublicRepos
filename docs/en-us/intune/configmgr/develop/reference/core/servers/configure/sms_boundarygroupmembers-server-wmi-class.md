<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroupmembers-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_BoundaryGroupMembers Server WMI Class

The `SMS_BoundaryGroupMembers` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents boundary group members.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_BoundaryGroupMembers : SMS_BaseClass
{
    UInt32 BoundaryID;
    UInt32 GroupID;
};
```

## Methods

The `SMS_BoundaryGroupMembers` class does not define any methods.

## Properties

`BoundaryID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Unique identifier of the boundary.

`GroupID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Unique identifier for the boundary group.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes)
