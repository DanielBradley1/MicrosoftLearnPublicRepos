<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/formatsystemmessage-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# FormatSystemMessage Method

The `FormatSystemMessage` method, in Configuration Manager, formats a system error message by using the error code and optional insertion strings.

## Syntax

```
[VBScript]
SMSFormatMessageCtl.FormatSystemMessage
```

#### Parameters

`MessageID` Data type: `int`

Error message ID.

`InsertionStrings` Data type: `object`

Optional list of insertion strings.

## Return Value

A string.

## Requirements

FormatMessageCtl.dll.

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMSFormatMessageCtl Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smsformatmessagectl-class)
