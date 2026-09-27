<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/setallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetAllUpdatesUserExperience Method in Class CCM\_SoftwareUpdatesManager

The `SetAllUpdatesUserExperience` WMI class method, in Configuration Manager, sets the user experience mode that determines how software updates are displayed on a target computer.

Note

This method can be used to hide or show all software updates in software center.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 SetAllUpdatesUserExperience(
     [IN]  UInt32 UserExperience
);
```

#### Parameters

`UserExperience` Data type: `UInt32`

Qualifiers: \[in\]

The user experience flag. The following table shows the possible user experience mode values.

| Value | User experience |
| --- | --- |
| 0 | DEFAULT \(per policy\) |
| 1 | INTERACTIVE |
| 2 | QUIET |

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

This method is only available for local administrators. When a software update deployment has been prepared and software updates are available for installation, this method and the `GetAllUpdatesUserExperience` method can be used to configure the user experience.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[CCM\_SoftwareUpdatesManager Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwareupdatesmanager-client-wmi-class)
