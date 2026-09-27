<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/setautoinstallrequiredsoftwaretononbusinesshours-method -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# SetAutoInstallRequiredSoftwaretoNonBusinessHours Method in Class CCM\_ClientUXSettings

The `SetAutoInstallRequiredSoftwaretoNonBusinessHours` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that sets the value for `AutomaticallyInstallSoftware`.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 SetAutoInstallRequiredSoftwaretoNonBusinessHours
{
    [IN]    Boolean AutomaticallyInstallSoftware
};
```

## Parameters

`AutomaticallyInstallSoftware` Data type: `Boolean`

Qualifiers: \[id\("0"\), in\]

`true` if necessary software should be automatically installed during nonbusiness hours.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
