<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagetoadvert_a-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_PackageToAdvert\_a Server WMI Class

The `SMS_PackageToAdvert_a` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that relates an [SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class) object to the [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) object that it advertises.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_PackageToAdvert_a : SMS_BaseAssociation
{
      ref:SMS_Advertisement advert;
      ref:SMS_Package package;
};
```

## Methods

The `SMS_PackageToAdvert_a` class does not define any methods.

## Properties

`advert` Data type: `ref:SMS_Advertisement`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class) object path.

`package` Data type: `ref:SMS_Package`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) object path.

## Remarks

Class qualifiers for this class include:

- Association: ToInstance
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class) [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class)
