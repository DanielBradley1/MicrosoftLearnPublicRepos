<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectiontopkgadvert_a-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CollectionToPkgAdvert\_a Server WMI Class

The `SMS_CollectionToPkgAdvert_a` association Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that uses the `CollectionID` property to relate an [SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class) object with its target [SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) object.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionToPkgAdvert_a : SMS_BaseAssociation
{
      ref:SMS_Advertisement advert;
      ref:SMS_Collection collection;
};
```

## Methods

The `SMS_CollectionToPkgAdvert_a` class does not define any methods.

## Properties

`advert` Data type: `ref:SMS_Advertisement`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class) object path.

`collection` Data type: `ref:SMS_Collection`

Access type: Read/Write

Qualifiers: \[key\]

Reference to an [SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) object path.

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
