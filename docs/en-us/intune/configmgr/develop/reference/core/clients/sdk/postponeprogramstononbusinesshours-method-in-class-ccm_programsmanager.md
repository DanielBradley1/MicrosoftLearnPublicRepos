<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/postponeprogramstononbusinesshours-method-in-class-ccm_programsmanager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# PostponeProgramsToNonBusinessHours Method in Class CCM\_ProgramsManager

The `PostponeProgramsToNonBusinessHours` WMI class method, in Configuration Manager, schedules legacy software distribution programs to run in the next available user defined service window.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 PostponeProgramsToNonBusinessHours(
     [IN]  CCM_Program CCMPrograms[],
     [IN]  Boolean RebootImmediatelyAfterInstall
);
```

#### Parameters

`CCMPrograms []` Data type: `CCM_Program`

Qualifiers: \[in\]

Array of software distribution programs to be postponed.

`RebootImmediatelyAfterInstall` Data type: `Boolean`

Qualifiers: \[in\]

`true` if the computer restarts immediately after the installation, otherwise, `false`.

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

[CCM\_ProgramsManager Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_programsmanager-client-wmi-class)
