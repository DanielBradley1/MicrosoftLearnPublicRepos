<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_powermanagementclientoptoutsetting-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_PowerManagementClientOptoutSetting Client WMI Class

The `CCM_PowerManagementClientOptoutSetting` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the settings that allow users to exclude their device from power management.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_PowerManagementClientOptoutSetting :
{
    Boolean AdminAllowOptout;
    Boolean EffectiveClientOptOut;
    Boolean IsClientOptOut;
};
```

## Methods

The `CCM_PowerManagementClientOptoutSetting` class does not define any methods.

## Properties

`AdminAllowOptOut` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the Admin allows users to exclude their device from power management.

`EffectiveClientOptOut` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the result of AdminAllowOptOut and IsClientOptOut is ClientOptOut.

`IsClientOptOut` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the user has excluded their device from power management.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
