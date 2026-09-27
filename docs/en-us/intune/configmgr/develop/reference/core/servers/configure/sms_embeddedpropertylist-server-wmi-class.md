<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_EmbeddedPropertyList Server WMI Class

The `SMS_EmbeddedPropertyList` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class in Configuration Manager that represents a general-purpose embedded object that defines property lists. The property lists are used by the site control file to define the string array properties of a site control item.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_EmbeddedPropertyList
{
     String ItemType;
     String PropertyListName;
     String Values[];
}
```

## Methods

The `SMS_EmbeddedPropertyList` class doesn't define any methods.

## Properties

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

Property list token item, site control file.

`PropertyListName` Data type: `String`

Access type: Read/Write

Qualifiers: None

Name of the property list. The name is case sensitive and might contain several words, for example, "Network Connection Accounts". The default value is "".

`Values` Data type: `String` Array

Access type: Read/Write

String values for the property list. For example, "SITE\_DEFN\_NETWK\_CONN\_ACCNTS" is the value corresponding to the property list name "Network Connection Accounts". The default value is "".

## Remarks

Class qualifiers for this class include:

- Embedded

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  There is no list that defines the properties for each site control item. The best way to determine the properties for each site control item is to follow the steps defined in `Determining Which Site Control Item to Use`. Property names that contain the word Reserved cannot be modified.

  Arrays of strings that come from the system registry use the [SMS\_Client\_Reg\_MultiString\_List Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_client_reg_multistring_list-server-wmi-class) class.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Site Configuration Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_Client\_Reg\_MultiString\_List Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_client_reg_multistring_list-server-wmi-class) [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class) [About the site control file](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file)
