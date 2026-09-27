<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitetositeid_a-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SiteToSiteID\_a Server WMI Class

The `SMS_SiteToSiteID_a` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that relates an [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class) object with an [SMS\_Identification Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class) object representing identifying information for the site.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SiteToSiteID_a : SMS_BaseAssociation
{
      ref:SMS_Site site;
      ref:SMS_Identification siteIdentification;
};
```

## Methods

The `SMS_SiteToSiteID_a` class does not define any methods.

## Properties

`site` Data type: `ref:SMS_site`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class) object path for the site.

`siteIdentification` Data type: `ref:SMS_Identification`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_Identification Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class) object path for the site identification.

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
