<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_scftosite_a-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SCFToSite\_a Server WMI Class

The `SMS_SCFToSite_a` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that uses the `SiteCode` property to relate [SMS\_SiteControlFile Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolfile-server-wmi-class) objects to [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class) objects.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SCFToSite_a : SMS_BaseAssociation
{
      ref:SMS_Site Site;
      ref:SMS_SiteControlFile SiteControlFile;
};
```

## Properties

`Site` Data type: `ref:SMS_Site`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class) object path.

`SiteControlFile` Data type: `ref:SMS_SiteControlFile`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_SiteControlFile Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolfile-server-wmi-class)object path.

## Remarks

Class qualifiers for this class include:

- Association: ToInstance
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes)
