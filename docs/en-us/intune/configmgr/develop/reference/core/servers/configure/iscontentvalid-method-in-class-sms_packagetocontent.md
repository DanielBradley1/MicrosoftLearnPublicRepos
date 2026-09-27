<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iscontentvalid-method-in-class-sms_packagetocontent -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IsContentValid Method in Class SMS\_PackageToContent

The `IsContentValid` Windows Management \(WMI\) class method, in Configuration Manager, determines if the package content is valid.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
Boolean IsContentValid();
```

#### Parameters

None.

## Return Values

A `Boolean` data type that is `true` if the package contains all the files for the content; otherwise `false`.

## Remarks

This method checks the package to ensure that all files are available for the content. It also checks to ensure that the licensing terms are met.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_PackageToContent Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagetocontent-server-wmi-class)
