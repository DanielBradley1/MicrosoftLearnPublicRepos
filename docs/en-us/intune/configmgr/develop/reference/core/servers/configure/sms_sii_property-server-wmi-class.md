<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sii_property-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SII\_Property Server WMI Class

The `SMS_SII_Property` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a general-purpose storage object for property data that can be represented as a single integer or two strings.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SII_Property : SMS_SiteInstallItem
{
     String ItemName;
     String ItemType;
     String PropertyName;
     UInt32 Value;
     String Value1;
     String Value2;
};
```

## Methods

The `SMS_SII_Property` class does not define any methods.

## Properties

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteInstallItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteInstallItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitem-server-wmi-class).

`PropertyName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the property. The name is case sensitive and might contain several words, for example, "Connection Point".

`Value` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

A numeric value if the property is numeric.

`Value1` Data type: `String`

Access type: Read/Write

Qualifiers: None

A string value if the property is a string. The value is a registry data type if the property comes from the system registry. Otherwise, the value is the actual string for the property.

`Value2` Data type: `String`

Access type: Read/Write

Qualifiers: None

A value to indicate the string value of the property if `Value1` indicates a `REG_SZ` registry data type.

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

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_SiteInstallItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitem-server-wmi-class)
