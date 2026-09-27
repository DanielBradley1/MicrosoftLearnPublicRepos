<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SCI\_ClientComp Server WMI Class

The `SMS_SCI_ClientComp` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the component to install on a client computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_ClientComp : SMS_SiteControlItem
{
     String ClientComponentName;
     UInt32 FileType;
     UInt32 Flags;
     String ItemName;
     String ItemType;
     SMS_EmbeddedPropertyList PropLists[];
     SMS_EmbeddedProperty Props[];
     SMS_Client_Reg_MultiString_List RegMultiStringLists[];
     String SiteCode;
};
```

## Methods

The `SMS_SCI_ClientComp` class does not define any methods.

## Properties

`ClientComponentName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the client component. The default value is "".

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key, enumeration:ToSubClass\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`Flags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits\]

Client component flag identifying whether a component is enabled or not. Possible values are:

| Value | Enabled flag |
| --- | --- |
| 0 | Not enabled |
| 1 | Enabled |

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`PropLists` Data type: `SMS_EmbeddedPropertyList` Array

Access type: Read/Write

Qualifiers: None

[SMS\_EmbeddedPropertyList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class) objects for the configuration.

`Props` Data type: `SMS_EmbeddedProperty` Array

Access type: Read/Write

Qualifiers: None

[SMS\_EmbeddedProperty Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedproperty-server-wmi-class) objects for the configuration.

`RegMultiStringLists` Data type: `SMS_Client_Reg_MultiString_List` Array

Access type: Read/Write

Qualifiers: None

[SMS\_Client\_Reg\_MultiString\_List Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_client_reg_multistring_list-server-wmi-class) objects for the configuration.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: \[key, SizeLimit\("3"\)\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

Run the following query for a complete list of client components defined for your site server.

```
SELECT * FROM SMS_SCI_ClientComp
WHERE SiteCode = "<sitecode>"
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_Client\_Reg\_MultiString\_List Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_client_reg_multistring_list-server-wmi-class) [SMS\_EmbeddedProperty Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedproperty-server-wmi-class) [SMS\_EmbeddedPropertyList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class) [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class)
