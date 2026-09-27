<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/requestcatalogupdate-method-in-class-sms_aiproxy -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RequestCatalogUpdate Method in Class SMS\_AIProxy

The `RequestCatalogUpdate` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, synchronizes the Asset Intelligence catalog with the System Center Online service.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 RequestCatalogUpdate(
     string ProxyName
);
```

#### Parameters

`ProxyName` Data type: `String`

Qualifiers: \[in\]

The `SMS_AIProxy` server name. This is located in the `ProxyName` property.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_AIProxy Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aiproxy-server-wmi-class)
