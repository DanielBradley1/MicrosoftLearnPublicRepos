<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/executeprograms-method-in-class-ccm_programsmanager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ExecutePrograms Method in Class CCM\_ProgramsManager

The `ExecutePrograms` WMI class method, in Configuration Manager, manages downloads of legacy software distribution programs.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 ExecutePrograms(
     [IN]  CCM_Program CCMPrograms[],
     [IN]  String SDKCallerId
);
```

#### Parameters

`CCMPrograms[]` Data type: `CCM_Program`

Qualifiers: \[in\]

Array of software distribution programs to download.

`SDKCallerId` Data type: `String`

Qualifiers: \[in\]

Identifier of the caller.

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
