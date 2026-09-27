<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getdeviceid-method-in-class-ccm_softwarecatalogutilities -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetDeviceId Method in Class CCM\_SoftwareCatalogUtilities

The `GetDeviceId` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that returns the device \(client\) identifier.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetDeviceId
{
    [OUT]   String ClientId
    [OUT]   String SignedClientId
};
```

## Parameters

`ClientId` Data type: `String`

Qualifiers: \[id\("0"\), out\]

Client identifier.

`SignedClientId` Data type: `String`

Qualifiers: \[id\("1"\), out\]

Signed client identifier.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
