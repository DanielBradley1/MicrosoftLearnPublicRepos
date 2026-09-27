<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getclientversion-method-in-class-ccm_softwarecatalogutilities -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetClientVersion Method in Class CCM\_SoftwareCatalogUtilities

The `GetClientVersion` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, that returns the client version.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetClientVersion
{
    [OUT]   String ClientVersion
};
```

## Parameters

`ClientVersion` Data type: `String`

Qualifiers: \[id\("0"\), out\]

Version number of the installed client software.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
