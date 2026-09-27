<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getcurrentwindowavailabletime-method-in-class-ccm_servicewindowmanager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetCurrentWindowAvailableTime Method in Class CCM\_ServiceWindowManager

The `GetCurrentWindowAvailableTime` WMI class method, in Configuration Manager, gets the time remaining in a currently active service window for a specified type.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetCurrentWindowAvailableTime(
     [IN]  UInt32 ServiceWindowType,
     [IN]  Boolean FallbackToAllProgramsWindow,
     [OUT] UInt32 WindowAvailableTime
);
```

#### Parameters

`ServiceWindowType` Data type: `UInt32`

Qualifiers: \[in\]

Type of service window. The following table shows the list of possible values.

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

`WindowAvailableTime` Data type: `UInt32`

Qualifiers: \[out\]

Available time remaining for service window.

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
