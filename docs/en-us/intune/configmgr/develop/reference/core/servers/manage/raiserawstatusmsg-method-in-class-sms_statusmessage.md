<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/raiserawstatusmsg-method-in-class-sms_statusmessage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RaiseRawStatusMsg Method in Class SMS\_StatusMessage

The `RaiseRawStatusMsg` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, creates a status message from an external message DLL.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 RaiseRawStatusMsg(
   String ModuleName,
   UInt32 MessageType,
   UInt32 MessageID,
   UInt32 Win32Error,
   UInt32 ProcessID,
   UInt32 ThreadID,
   DateTime Time,
   UInt32 AttrIDs[],
   String AttrValues[],
   String TopLevelSiteCode
);
```

#### Parameters

`ModuleName` Data type: `String`

Qualifiers: \[in\]

The name of the DLL module.

`MessageType` Data type: `UInt32`

Qualifiers: \[in\]

The message type. Possible values are defined by the `MessageType` property of [SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class).

`MessageID` Data type: `UInt32`

Qualifiers: \[in, Range\("0-65535"\)\]

ID of the message. See the `MessageID` property of [SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class).

`Win32Error` Data type: `UInt32`

Qualifiers: \[in, optional\]

Win32 error code associated with the status message.

`ProcessID` Data type: `UInt32`

Qualifiers: \[in, optional\]

ID of the process that created the message. The default value is 0.

`ThreadID` Data type: `UInt32`

Qualifiers: \[in, optional\]

ID of the thread that created the message. The default value is 0.

`Time` Data type: `DateTime`

Qualifiers: \[in, optional\]

Date and time, in Universal Coordinated Time \(UTC\), when the status message was created. The default value indicates current time.

`AttrIDs` Data type: `UInt32` Array

Qualifiers: \[in, optional\]

IDs of message attributes.

`AttrValues` Data type: `String` Array

Qualifiers: \[in, optional\]

Values of message attributes.

`TopLevelSiteCode` Data type: `String`

Qualifiers: \[in, optional\]

This property is deprecated.

## Return Values

A `UInt32` data type.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class)
