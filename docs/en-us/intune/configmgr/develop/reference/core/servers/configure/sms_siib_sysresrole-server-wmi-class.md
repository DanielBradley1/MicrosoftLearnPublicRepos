<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siib_sysresrole-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SIIB\_SysResRole Server WMI Class

The `SMS_SIIB_SysResRole` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a system role associated with a Configuration Manager console property page resource.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SIIB_SysResRole : SMS_SiteInstallItemBase
{
   String ChmFile;
   UInt32 DescriptionID;
   UInt32 DispIconID;
   UInt32 DispNameID;
   UInt32 Flags;
   String GUID;
   String HtmFile;
   String ItemName;
   String ItemType;
   String ResDLL;
   String RoleName;
   String SiteCode;
   String Units[];
};
```

## Methods

The `SMS_SIIB_SysResRole` class does not define any methods.

## Properties

`ChmFile` Data type: `String`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`DescriptionID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`DispIconID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`DispNameID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`Flags` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[bits\]

Role flags. Currently the only supported flag is ASSIGNABLE \(0\).

| Bit | Description |
| --- | --- |
| 0 | ASSIGNABLE |

`GUID` Data type: `String`

Access type: Read-only

Qualifiers: None

GUID representing the Microsoft Management Console node for the property page.

`HtmFile` Data type: `String`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

`ResDLL` Data type: `String`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`RoleName` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the role.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

`Units` Data type: `String` Array

Access type: Read-only

Qualifiers: None

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class)
