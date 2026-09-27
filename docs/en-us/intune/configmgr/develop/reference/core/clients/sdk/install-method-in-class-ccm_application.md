<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/install-method-in-class-ccm_application -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Install Method in Class CCM\_Application

The `Install` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, that installs an application.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 Install
{
    [IN]    String Id
    [IN]    String Revision
    [IN]    Boolean IsMachineTarget
    [IN]    UInt32 EnforcePreference
    [IN]    String Priority
    [IN]    Boolean IsRebootIfNeeded
    [OUT]   String JobId
};
```

## Parameters

`Id` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Application identifier.

`Revision` Data type: `String`

Qualifiers: \[id\("1"\), in\]

Revision.

`IsMachineTarget` Data type: `Boolean`

Qualifiers: \[id\("2"\), in\]

`true` if the application targets a device.

`EnforcePreference` Data type: `UInt32`

Qualifiers: \[id\("3"\), in, values\]

Enforce preference. Possible values are:

| Value | Enforce preference |
| --- | --- |
| 0 | Immediate |
| 1 | NonBusinessHours |
| 2 | AdminSchedule |

`Priority` Data type: `String`

Qualifiers: \[id\("4"\), in, valuemap\]

Priority. Possible values are:

| Value |
| --- |
| Foreground |
| High |
| Normal |
| Low |

`IsRebootIfNeeded` Data type: `Boolean`

Qualifiers: \[id\("5"\), in\]

`true` if a reboot is needed.

`JobId` Data type: `String`

Qualifiers: \[id\("6"\), out\]

Job identifier.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
