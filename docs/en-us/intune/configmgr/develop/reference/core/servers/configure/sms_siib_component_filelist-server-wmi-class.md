<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siib_component_filelist-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SIIB\_Component\_FileList Server WMI Class

The `SMS_SIIB_Component_FileList` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents file list information for a Configuration Manager component.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SIIB_Component_FileList : SMS_SiteInstallItemBase
{
     String ComponentName;
     UInt64 Flags
     String ItemName;
     String ItemType;
     SMS_SII_PropertyList PropLists[];
     SMS_SII_Property Props[];
     String SiteCode;
     String Units[];
};
```

## Methods

The `SMS_SIIB_Component_FileList` class does not define any methods.

## Properties

`ComponentName` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the Configuration Manager component to which the file list corresponds.

`Flags` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[bits\]

For internal use only.

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: Key

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

`PropLists` Data type: `SMS_SII_PropertyList` Array

Access type: Read-only

Qualifiers: None

[SMS\_SII\_PropertyList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sii_propertylist-server-wmi-class) objects for the component.

`Props` Data type: `SMS_SII_Property` Array

Access type: Read-only

Qualifiers: None

[SMS\_SII\_Property Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sii_property-server-wmi-class) objects for the component.

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

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_SII\_Property Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sii_property-server-wmi-class) [SMS\_SII\_PropertyList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sii_propertylist-server-wmi-class) [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class)
