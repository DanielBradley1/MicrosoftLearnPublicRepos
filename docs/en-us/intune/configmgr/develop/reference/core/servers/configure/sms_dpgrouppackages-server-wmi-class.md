<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_dpgrouppackages-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DPGroupPackages Server WMI Class

The `SMS_DPGroupPackages` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents distribution point packages.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DPGroupPackages : SMS_BaseClass
{
    String GroupID;
    String PkgID;
};
```

## Methods

The `SMS_DPGroupPackages` class does not define any methods.

## Properties

`GroupID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Unique identifier for the distribution point group.

`PkgID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Package associated with the distribution point group.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
