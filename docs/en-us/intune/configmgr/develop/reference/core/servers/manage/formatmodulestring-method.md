<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/formatmodulestring-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# FormatModuleString Method

The `FormatModuleString` method, in Configuration Manager, loads string resources from the resource DLL.

## Syntax

```
[VBScript]
SMSFormatMessageCtl.FormatModuleString
```

#### Parameters

`ModuleName` Data type: `string`

Name of the module to load. The name can be Srvmsgs.dll, Provmsgs.dll, or Climmsgs.dll.

`MessageID` Data type: `int`

Message ID " combined by using the bitwise OR operation with the severity.

`InsertionStrings` Data type: `object`

Optional list of insertion strings.

## Return Value

A string.

## Remarks

`FormatModuleString` loads a string that is specified by `MessageID` from a string resource in the `ModuleName` module and inserts the supplied strings.

## Requirements

FormatMessageCtl.dll.

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMSFormatMessageCtl Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smsformatmessagectl-class)
