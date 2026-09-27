<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getautoinstallrequiredsoftwaretononbusinesshours-method -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# GetAutoInstallRequiredSoftwaretoNonBusinessHours Method in Class CCM\_ClientUXSettings

The `GetAutoInstallRequiredSoftwaretoNonBusinessHours` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that gets the value for `AutomaticallyInstallSoftware`.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetAutoInstallRequiredSoftwaretoNonBusinessHours
{
    [OUT]   Boolean AutomaticallyInstallSoftware
};
```

## Parameters

`AutomaticallyInstallSoftware` Data type: `Boolean`

Qualifiers: \[id\("0"\), out\]

`true` if necessary software should be automatically installed during nonbusiness hours.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
