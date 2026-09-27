<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/isusedcert-method-in-class-sms_site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IsUsedCert Method in Class SMS\_Site

The `IsUsedCert` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, verifies whether the specified certificate is used.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
Boolean IsUsedCert(
   String Certificate
);
```

#### Parameters

`Certificate` Data type: `String`

Qualifiers: \[in\]

The certificate to check against the site.

## Return Values

`true` if the specified certificate is used on the site; otherwise `false`.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class) [GetClientInfo Method in Class SMS\_Site](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getclientinfo-method-in-class-sms_site)
