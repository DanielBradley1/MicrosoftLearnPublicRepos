<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/isfuturewindowavailable-method-in-class-ccm_servicewindowmanager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IsFutureWindowAvailable Method in Class CCM\_ServiceWindowManager

The `IsFutureWindowAvailable` WMI class method, in Configuration Manager, determines whether a service window of a specified type and the given duration is going to be available.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 IsFutureWindowAvailable(
     [IN]  UInt32 ServiceWindowType,
     [IN]  Boolean FallbackToAllProgramsWindow,
     [IN]  UInt32 MaxRuntime,
     [OUT] Boolean WillProgramRunInFuture
);
```

#### Parameters

`ServiceWindowType` Data type: `UInt32`

Qualifiers: \[in\]

Type of service window. The following table lists the possible values.

| Value | Service Window Type | Description |
| --- | --- | --- |
| 1 | ALLPROGRAM\_SERVICEWINDOW | All Programs Service Window |
| 2 | PROGRAM\_SERVICEWINDOW | Program Service Window |
| 3 | REBOOTREQUIRED\_SERVICEWINDOW | Reboot Required Service Window |
| 4 | SOFTWAREUPDATE\_SERVICEWINDOW | Software Update Service Window |
| 5 | OSD\_SERVICEWINDOW | OSD Service Window |
| 6 | USER\_DEFINED\_SERVICE\_WINDOW | Corresponds to non-working hours |

`FallbackToAllProgramsWindow` Data type: `Boolean`

Qualifiers: \[in\]

`true` if the generic **All programs window** service window is to be used when a window specified in `ServiceWindowType` is not available; otherwise, `false`.

`MaxRuntime` Data type: `UInt32`

Qualifiers: \[in\]

Maximum run time, in seconds, that a software update installation has to complete before the installation is no longer monitored by Configuration Manager. This setting is also used to determine whether there is enough time to install the update before the end of a maintenance window. The default setting is 60 minutes \(3600 seconds\) for service packs and 5 minutes \(300 seconds\) for all other software update types.

Important

Make sure that the maximum run time value is not set for more time than the configured maintenance window or the software update installation will not initiate.

`WillProgramRunInFuture` Data type: `Boolean`

Qualifiers: \[out\]

`true` if the specified service window is going to be available; otherwise, `false`.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[CCM\_ServicewindowManager Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_servicewindowmanager-client-wmi-class)
