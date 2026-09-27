<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/requestrefresh-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# RequestRefresh Method in Class SMS\_Collection

The `RequestRefresh` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, triggers a re-evaluation of collection membership by the Configuration Manager collection evaluator component.

The following syntax is simplified from Managed Object Format \(MOF\) code and is intended to show the definition of the method.

## Syntax

```
SInt32 RequestRefresh();
```

#### Parameters

Note

The previously available parameter `includesubcollections` has been deprecated in Configuration Manager.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
