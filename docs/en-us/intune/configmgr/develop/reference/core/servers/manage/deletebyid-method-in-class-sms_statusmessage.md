<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/deletebyid-method-in-class-sms_statusmessage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# DeleteByID Method in Class SMS\_StatusMessage

The `DeleteByID` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, deletes a group of up to 256 status messages.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 DeleteByID(
   SInt64 RecordIDs[]
);
```

#### Parameters

`RecordIDs` Data type: `SInt64` Array

Qualifiers: \[in, Max\(256\)\]

IDs for the records of the status messages to delete.

## Return Values

A `UInt32` data type that indicates the number of rows deleted.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class)
