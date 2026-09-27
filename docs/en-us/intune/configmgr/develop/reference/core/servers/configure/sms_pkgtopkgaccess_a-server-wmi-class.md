<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_pkgtopkgaccess_a-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_PkgToPkgAccess\_a Server WMI Class

The `SMS_PkgToPkgAccess_a` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that uses the `PackageID` property to relate an [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) object with the [SMS\_PackageAccessByUsers Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packageaccessbyusers-server-wmi-class) object used to access the package on its distribution points.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_PkgToPkgAccess_a : SMS_BaseAssociation
{
      ref:SMS_Package package;
      ref:SMS_PackageAccessByUsers pkgAccess;
};
```

## Methods

The `SMS_PkgToPkgAccess_a` class does not define any methods.

## Properties

`package` Data type: `ref:SMS_Package`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) object path.

`pkgAccess` Data type: `ref:SMS_PackageAccessByUsers`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_PackageAccessByUsers Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packageaccessbyusers-server-wmi-class) object path.

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

[SMS\_Package Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) [SMS\_PackageAccessByUsers Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packageaccessbyusers-server-wmi-class)
