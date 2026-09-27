<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_boundarygroupsitesystems-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_BoundaryGroupSiteSystems Server WMI Class

The `SMS_BoundaryGroupSiteSystems` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents site systems that serve computers within the boundary group.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_BoundaryGroupSiteSystems : SMS_BaseClass
{
    UInt32 Flags;
    UInt32 GroupID;
    String ServerNALPath;
    String SiteCode;
};
```

## Methods

The `SMS_BoundaryGroupSiteSystems` class does not define any methods.

## Properties

`Flags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits\]

Specifies the connection type of the boundary. Possible values are:

| Value | Description |
| --- | --- |
| 0 | FAST |
| 1 | SLOW |

Note

This parameter is no longer used for distribution points.

`GroupID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, read\]

Unique identifier of the boundary group.

`ServerNALPath` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

NAL path of site system servicing machines within the boundary.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: \[read, sizelimit\("3"\)\]

Site code of the role.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes)
