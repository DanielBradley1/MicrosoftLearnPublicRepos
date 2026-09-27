<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_lastcategoryobject-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_LastCategoryObject Server WMI Class

The `SMS_LastCategoryObject` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the object that has this assignment as the last category assignment.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_LastCategoryObject : SMS_BaseClass
{
    String CategoryID;
    String ObjectKey;
    UInt32 ObjectTypeID;
};
```

## Methods

The `SMS_LastCategoryObject` class does not define any methods.

## Properties

`CategoryID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

ID of the RBA security category.

`ObjectKey` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Object key.

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

ID of the object type.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
