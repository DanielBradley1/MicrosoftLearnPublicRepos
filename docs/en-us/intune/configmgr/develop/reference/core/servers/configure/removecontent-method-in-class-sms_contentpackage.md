<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/removecontent-method-in-class-sms_contentpackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RemoveContent Method in Class SMS\_ContentPackage

The `RemoveContent` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, removes the content for the given content ID from the package.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 RemoveContent(
     uint32  ContentIDs[],
     boolean bRefreshDPs[],
);
```

#### Parameters

`ContentIDs` Data type: `UInt32` Array

Qualifiers: `[in, optional]`

Content identifiers for content to be removed.

`bRefreshDPs` Data type: `Boolean` Array

Qualifiers: `[in]`

`true`, if distribution points should be refreshed. The default value is `true`.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Application Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_application-server-wmi-class)
