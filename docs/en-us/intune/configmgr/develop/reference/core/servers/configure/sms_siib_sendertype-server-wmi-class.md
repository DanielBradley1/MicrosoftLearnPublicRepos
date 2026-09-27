<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siib_sendertype-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_SIIB\_SenderType Server WMI Class

The `SMS_SIIB_SenderType` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the sender type for the associated Configuration Manager console property pages.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_SIIB_SenderType : SMS_SiteInstallItemBase
{
   String ChmFile;
   UInt32 DescriptionID;
   UInt32 DispIconID;
   UInt32 DispNameID;
   UInt32 Flags;
   String GUID;
   String HtmFile;
   String ItemName;
   String ItemType;
   String ResDLL;
   String SenderType;
   String SiteCode;
   String Units[];
};
```

## Methods

The `SMS_SIIB_SenderType` class does not define any methods.

## Properties

`ChmFile` Data type: `String`

Access type: Read-only

Qualifiers: None

Compressed .chm file containing the .htm file for the sender type.

`DescriptionID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Resource ID of the description.

`DispIconID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Resource ID of the display icon.

`DispNameID` Data type: `UInt32`

Access type: Read-only

Qualifiers: None

Resource ID of the display name.

`Flags` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[bits\]

Flags defining operations supported by the sender. Possible values are:

0 ALLOW\_ADD

1 ALLOW\_DELETE

2 ALLOW\_MODIFY

`GUID` Data type: `String`

Access type: Read-only

Qualifiers: None

GUID representing the Microsoft Management Console node for the property page.

`HtmFile` Data type: `String`

Access type: Read-only

Help file \(.htm\) for the sender type.

`ItemName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

`ItemType` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

`ResDLL` Data type: `String`

Access type: Read-only

Qualifiers: None

Name of the resource DLL containing the resource strings for `DescriptionID`, `DispIconID`, and `DispNameID`.

`SenderType` Data type: `String`

Access type: Read-only

Qualifiers: None

Sender service name.

`SiteCode` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

`Units` Data type: `String` Array

Access type: Read-only

Qualifiers: None

See [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class).

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

[Configuration Manager Hierarchy Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes) [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class)
