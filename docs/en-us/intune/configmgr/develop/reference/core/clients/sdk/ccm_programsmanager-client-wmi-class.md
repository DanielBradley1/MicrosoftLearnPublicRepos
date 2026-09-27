<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_programsmanager-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_ProgramsManager Client WMI Class

The `CCM_ProgamsManager` WMI class is a public client class, in Configuration Manager, that manages a specified software distribution program.

The following syntax is simplified from the Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
class CCM_ProgramsManager();
```

## Methods

The following table shows the methods in the `CCM_ProgamsManager` class.

| Method | Description |
| --- | --- |
| [CancelDownload Method in Class CCM\_ProgramsManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_programsmanager) | Cancels jobs that are downloading content that is required for legacy software distribution programs. |
| [ExecuteProgram Method in Class CCM\_ProgramsManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/executeprogram-method-in-class-ccm_programsmanager) | Manages the download of a legacy software distribution program. |
| [ExecutePrograms Method in Class CCM\_ProgramsManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/executeprograms-method-in-class-ccm_programsmanager) | Manages the download of a group of legacy software distribution programs. |
| [PostponeProgramsToNonBusinessHours Method in Class CCM\_ProgramsManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/postponeprogramstononbusinesshours-method-in-class-ccm_programsmanager) | Schedules legacy software distribution programs to run in the next available user-defined service window. |

## Properties

The `CCM_ProgamsManager` class does not define any properties.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
