<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpgroupmembers-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DPGroupMembers Server WMI Class

The `SMS_DPGroupMembers` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents distribution point group members.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DPGroupMembers : SMS_BaseClass
{
    String DPNALPath;
    String GroupID;
};
```

## Methods

The `SMS_DPGroupMembers` class does not define any methods.

## Properties

`DPNALPath` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Distribution point NAL path.

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Unique identifier of the distribution point group.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
