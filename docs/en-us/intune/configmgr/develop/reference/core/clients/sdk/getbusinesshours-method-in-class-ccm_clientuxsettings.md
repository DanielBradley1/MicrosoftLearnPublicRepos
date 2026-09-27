<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getbusinesshours-method-in-class-ccm_clientuxsettings -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# GetBusinessHours Method in Class CCM\_ClientUXSettings

The `GetBusinessHours` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that gets the values for business hours.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetBusinessHours
{
    [OUT]   UInt32 WorkingDays
    [OUT]   UInt32 StartTime
    [OUT]   UInt32 EndTime
};
```

## Parameters

`WorkingDays` Data type: `UInt32`

Qualifiers: \[id\("0"\), out\]

Working days.

`StartTime` Data type: `UInt32`

Qualifiers: \[id\("1"\), out\]

Start time.

`EndTime` Data type: `UInt32`

Qualifiers: \[id\("2"\), out\]

End time.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
