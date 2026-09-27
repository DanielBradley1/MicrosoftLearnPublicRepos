<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallmap-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SiteInstallMap Server WMI Class

The `SMS_SiteInstallMap` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the site install map, which describes the layout of all installed features.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteInstallMap : SMS_BaseClass
{
     String BuildNumber;
     UInt32 FileType;
     String FormatVersion;
     String IMapData;
};
```

## Methods

The following table lists the method in `SMS_SiteInstallMap`.

| Method | Description |
| --- | --- |
| [Refresh Method in Class SMS\_SiteInstallMap](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/refresh-method-in-class-sms_siteinstallmap) | Reloads the install map from the database, which repopulates the classes. |

## Properties

`BuildNumber` Data type: `String`

Access type: Read/Write

Qualifiers: \[lazy\]

Configuration Manager build number.

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Reserved. Initialized with a value of 1.

`FormatVersion` Data type: `String`

Access type: Read/Write

Qualifiers: \[lazy\]

Format version of the install map.

`IMapData` Data type: `String`

Access type: Read-only

Qualifiers: \[large, lazy\]

Install map data in text format.

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Use classes derived from [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class) to view the install map.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class)
