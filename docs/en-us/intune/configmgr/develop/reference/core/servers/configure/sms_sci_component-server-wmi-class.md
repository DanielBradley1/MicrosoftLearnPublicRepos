<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_component-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SCI\_Component Server WMI Class

The `SMS_SCI_Component` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a Configuration Manager server component installed on one or more servers at a site.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SCI_Component : SMS_SiteControlItem
{
     String ComponentName;
     UInt32 FileType;
     UInt32 Flag;
     String ItemName;
     String ItemType;
     String Name;
     SMS_EmbeddedProperty Props[];
     SMS_EmbeddedPropertyList PropLists[];
     String SiteCode;
};
```

## Methods

The `SMS_SCI_Component` class does not define any methods.

## Properties

`ComponentName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the Configuration Manager server component. The default value is "".

`FileType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key, enumeration:ToSubClass\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`Flag` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Flag identifying the component. Possible values are listed below. The default value is NAMED\_SERVER\_INSTALLED \(6\).

| Value | Description |
| --- | --- |
| 1 | ROLE\_NOT\_INSTALLED. If the flag is set to this value, the `Name` property specifies the server role. The component is installed on every server having the specified role. |
| 2 | NAMED\_SERVER\_NOT\_INSTALLED. If the flag is set to this value, the `Name` property specifies a particular server on which the component is installed. The server name does not include backslashes. |
| 5 | ROLE\_INSTALLED. If the flag is set to this value, the `Name` property specifies the server role. The component is installed on every server having the specified role. |
| 6 | NAMED\_SERVER\_INSTALLED. If the flag is set to this value, the `Name` property specifies a particular server on which the component is installed. The server name does not include backslashes. |

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

Configuration Manager role or server name, depending on the value of `Flag`. The default value is "".

`Props` Data type: `SMS_EmbeddedProperty` Array

Access type: Read/Write

Qualifiers: None

[SMS\_EmbeddedProperty Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedproperty-server-wmi-class) objects for the component.

`PropLists` Data type: `SMS_EmbeddedPropertyList` Array

Access type: Read/Write

Qualifiers: None

[SMS\_EmbeddedPropertyList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class) objects for the component.

`SiteCode` Data type: `String`

Access type: Read/Write

Qualifiers: \[key, SizeLimit\("3"\)\]

See [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

Run the following query for a complete list of Configuration Manager server components defined for your site server.

```
SELECT * FROM SMS_SCI_Component
WHERE SiteCode = "<sitecode>"
```

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_EmbeddedProperty Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedproperty-server-wmi-class) [SMS\_EmbeddedPropertyList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class) [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class)
