<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getportalurlvalue-method-in-class-ccm_softwarecatalogutilities -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetPortalUrlValue Method in Class CCM\_SoftwareCatalogUtilities

The `GetPortalUrlValue` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that returns the portal url for a client.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetPortalUrlValue
{
    [OUT]   String PortalUrl
};
```

## Parameters

`PortalUrl` Data type: `String`

Qualifiers: \[id\("0"\), out\]

Portal url.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
