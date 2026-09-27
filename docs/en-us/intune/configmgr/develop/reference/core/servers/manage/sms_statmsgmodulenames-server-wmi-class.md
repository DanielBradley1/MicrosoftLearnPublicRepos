<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statmsgmodulenames-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_StatMsgModuleNames Server WMI Class

The `SMS_StatMsgModuleNames` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that maps module names to the message DLL that contains the status message text.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_StatMsgModuleNames : SMS_BaseClass
{
    String ModuleName;
    String MsgDLLName;
};
```

## Methods

The `SMS_StatMsgModuleNames` class does not define any methods.

## Properties

`ModuleName` Data type: `String`

Access type: Read

Qualifiers: \[key, not\_null\]

Module name as used in the `ModuleName` property of [SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class).

`MsgDLLName` Data type: `String`

Access type: Read

Qualifiers: None

Name of the corresponding resource DLL that contains the text of the message.

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class)
