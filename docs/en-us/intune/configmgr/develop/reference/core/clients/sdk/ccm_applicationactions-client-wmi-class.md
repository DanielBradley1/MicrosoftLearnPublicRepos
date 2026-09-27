<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_applicationactions-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_ApplicationActions Client WMI Class

The `CCM_ApplicationActions` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents application actions.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_ApplicationActions :
{
    DateTime NextGlobalRevalTime;
    DateTime NextRetryTime;
    DateTime NextServiceWindowTime;
};
```

## Methods

The `CCM_ApplicationActions` class does not define any methods.

## Properties

`NextGlobalRevalTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Next global reevaluation time.

`NextRetryTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Next retry time

`NextServiceWindowTime` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Next service window time.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
