<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/isofficecontent-method-in-class-sms_content -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IsOfficeContent Method in Class SMS\_Content

The `IsOfficeContent` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, specifies whether content is Microsoft 365 content.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
Boolean IsOfficeContent (
    UInt32 ContentId
);
```

#### Parameters

`ContentId` Data type: `UInt32`

Qualifiers: \[in\]

Content ID.

## Return Values

`True` if content is Microsoft 365 content; otherwise, `False`.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_Content server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_content-server-wmi-class)
