<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getusercapability-method-in-class-ccm_clientutilities -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetUserCapability Method in Class CCM\_ClientUtilities

The `GetUserCapability` Windows Management Instrumentation \(WMI\) class method in Configuration Manager.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetUserCapability
{
    [IN]    UInt32 Feature
    [OUT]   UInt32 Value
};
```

## Parameters

`Feature` Data type: `UInt32`

Qualifiers: \[id\("0"\), in\]

Feature.

`Value` Data type: `UInt32`

Qualifiers: \[id\("1"\), out\]

Value.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
