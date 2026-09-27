<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_client_reg_multistring_list-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_Client\_Reg\_MultiString\_List Server WMI Class

The `SMS_Client_Reg_MultiString_List` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager that represents a list of client registry multi-string items from the site control file.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_Client_Reg_MultiString_List
{
     String ItemType;
     String ValueName;
     String KeyPath;
     String ValueStrings[];
};
```

## Methods

The `SMS_Client_Reg_MultiString_List` class doesn't define any methods.

## Properties

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

Client registry multstring item type.

`ValueName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Property name reflected in the system registry key where the multi-string items are stored. The default value is "".

`KeyPath` Data type: `String`

Access type: Read/Write

Qualifiers: None

Path to the multi-string item. The default value is "".

Note

Do not set this property when updating the `ValueName` property.

`ValueStrings` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

List of strings that serve as registry data values. The meaning of the strings is determined by the `ValueName` property.

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  This class behaves the same as [SMS\_EmbeddedPropertyList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class). It's used to represent data that is stored in the system registry with the `REG_MULTI_SZ` data type.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_EmbeddedPropertyList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class)
