<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_inventoryclassproperty-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_InventoryClassProperty Server WMI Class

The `SMS_InventoryClassProperty` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, embedded in the `SMS_InventoryClass` that represents the properties associated with an inventory class in Configuration Manager.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_InventoryClassProperty :
{
    UInt32 IsKey;
    String PropertyName;
    String SMSDeviceUri;
    UInt32 Type;
    String Units;
};
```

## Methods

The `SMS_InventoryClassProperty` class does not define any methods.

## Properties

`IsKey` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

`true`, if this property is the key of the class. The default value is `false`.

`PropertyName` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

The name of the property. The default value is an empty string.

`SMSDeviceUri` Data type: `String`

Access type: Read/Write

Qualifiers: none

SMS device URI in XML format. This can support multiple device URIs.

`Type` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

CIMv2 type of property.

`Units` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

The units of the property.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
