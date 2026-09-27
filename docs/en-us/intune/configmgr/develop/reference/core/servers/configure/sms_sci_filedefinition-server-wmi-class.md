<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_filedefinition-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SCI\_FileDefinition Server WMI Class

The `SMS_SCI_FileDefinition` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the basic properties of the site control file.

Note

This class is vital to the operation of the site control infrastructure. Changing the values for an existing site might render the site control file unusable for further configuration. Existing objects for functioning sites should not be changed.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_FileDefinition : SMS_SiteControlItem
{
     String Comment;
     UInt32 FileType;
     String ItemName;
     String ItemType;
     String OriginatingSite;
     UInt32 SerialNumber;
     String SiteCode;
     String TargetSite;
};
```

## Methods

The `SMS_SCI_FileDefinition` class doesn't define any methods.

## Properties

`Comment` Data type: `String`

Access type: Read/Write

Qualifiers: None

Free-format comment. The default value is "".

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key, enumeration:ToSubClass\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`OriginatingSite` Data type: `String`

Access type: Read-only

Qualifiers: None

Site that originated the creation of the value indicated by `TargetSite`. The default value is "".

`SerialNumber` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Serial number of the actual site control file. It's incremented each time the site control file changes.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: \[key, SizeLimit\("3"\)\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`TargetSite` Data type: `String`

Access type: Read/Write

Qualifiers: None

Site for which you're creating the site control file. The default value is "".

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class)
