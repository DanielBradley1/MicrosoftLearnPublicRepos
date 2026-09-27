<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getsuppresscomputeractivityinpresentationmode-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetSuppressComputerActivityInPresentationMode Method in Class CCM\_ClientUXSettings

The `GetSuppressComputerActivityInPresentationMode` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, that gets the value for `SuppressComputerActivityInPresentationMode`

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetSuppressComputerActivityInPresentationMode
{
    [OUT]   Boolean SuppressComputerActivityInPresentationMode
};
```

## Parameters

`SuppressComputerActivityInPresentationMode` Data type: `Boolean`

Qualifiers: \[id\("0"\), out\]

`true` to suppress computer activity in presentation mode.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
