<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siib_configuration-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SIIB\_Configuration Server WMI Class

The `SMS_SIIB_Configuration` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the configuration for a property page in the Configuration Manager console.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SIIB_Configuration : SMS_SiteInstallItemBase
{
   String ChmFile;
   String ConfigUnitName;
   String ConfigurationName;
   UInt32  DescriptionID;
   UInt32  DispIconID;
   UInt32  DispNameID;
   UInt32  Flags;
   String GUID;
   String HtmFile;
   String ItemName;
   String ItemType;
   String ResDLL;
   String SiteCode;
   String Type;
   String Units[];
};
```

## Methods

The `SMS_SIIB_Configuration` class does not define any methods.

## Properties

`ChmFile` Data type: `String`

Access type: Read-only

Qualifiers: None

This property is deprecated.

`ConfigUnitName` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the configuration unit to find in the site control file.

`ConfigurationName` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the configuration.

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

This property is deprecated.

`Flags` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[bits\]

Flags defining the site to which the configuration applies. Possible values are listed below. The default value is 3.

0 SECONDARY

1 PRIMARY

`GUID` Data type: `String`

Access type: Read-only

Qualifiers: None

This property is deprecated.

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

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

`Type` Data type: `String`

Access type: Read-only

Qualifiers: None

The configuration type. Possible values are:

- COMPONENT\_CONFIGURATION\(Component Configuration\)
- DISCOVERY\_METHOD\(Discovery Method\)
- CLIENT\_SETUP\_METHOD\(Client Setup Method\)
- INVENTORY\_METHOD\(Inventory Method\)
- CLIENT\_AGENT\(Client Agent\)
- CLIENT\_ACCOUNT\_CONFIGURATION\(Client Account Configuration\)
- SERVER\_ACCOUNT\_CONFIGURATION\(Server Account Configuration\)

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
