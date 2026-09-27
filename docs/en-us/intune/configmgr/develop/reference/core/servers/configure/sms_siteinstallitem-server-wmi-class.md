<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitem-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SiteInstallItem Server WMI Class

The `SMS_SiteInstallItem` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the abstract base class of all site install item classes.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteInstallItem : SMS_BaseClass
{
     String ItemName;
     String ItemType;
};
```

## Methods

The `SMS_SiteInstallItem` class does not define any methods.

## Properties

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

Unique name identifying a site install item within items of the same type.

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

Unique type identifying a site install item.

## Remarks

Class qualifiers for this class include:

- Abstract

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Your application uses classes derived from this class to manipulate site install items. These classes are named with the prefix "SMS\_SII\_". An example of a derived class is [SMS\_SII\_Property Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sii_property-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes)
