<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/determineifrebootpending-method-in-class-ccm_clientutilities -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# DetermineIfRebootPending Method in Class CCM\_ClientUtilities

The `DetermineIfRebootPending` Windows Management Instrumentation \(WMI\) class method in Configuration Manager.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 DetermineIfRebootPending
{
    [OUT]   Boolean RebootPending
    [OUT]   Boolean IsHardRebootPending
    [OUT]   Boolean InGracePeriod
    [OUT]   DateTime DisableHideTime
    [OUT]   DateTime RebootDeadline
};
```

## Parameters

`RebootPending` Data type: `Boolean`

Qualifiers: \[id\("0"\), out\]

RebootPending.

`IsHardRebootPending` Data type: `Boolean`

Qualifiers: \[id\("1"\), out\]

IsHardRebootPending.

`InGracePeriod` Data type: `Boolean`

Qualifiers: \[id\("2"\), out\]

InGracePeriod.

`DisableHideTime` Data type: `DateTime`

Qualifiers: \[id\("3"\), out\]

DisableHideTime.

`RebootDeadline` Data type: `DateTime`

Qualifiers: \[id\("4"\), out\]

RebootDeadline.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
