<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/setpowermanagementsettings-method-in-class-ccm_powermanagementsettings -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetPowerManagementSettings Method in Class CCM\_PowerManagementSettings

The `SetPowerManagementSettings` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, that sets power management settings on a client.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
sint32 SetPowerManagementSettings
{
    [IN]  Boolean IsOptOutFromPowerPlan;
    [OUT] UInt32 ReturnValue;
};
```

## Parameters

`IsOptOutFromPowerPlan` Data type: `Boolean`

Qualifiers: \[id\("0"\), in\]

`true` to allow users to exclude their device from power management.

`ReturnValue` Data type: `UInt32`

Qualifiers: \[out\]

Return value.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
