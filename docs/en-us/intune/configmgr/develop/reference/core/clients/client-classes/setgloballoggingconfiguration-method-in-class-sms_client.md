<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setgloballoggingconfiguration-method-in-class-sms_client -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# SetGlobalLoggingConfiguration Method in Class SMS\_Client

The `SetGlobalLoggingConfiguration` method, in Configuration Manager, defines the global logging configuration for the client. This configuration represents either component-level logging or default logging if component-level logging isn't defined.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 SetGlobalLoggingConfiguration(
     UInt32 LogLevel,
     UInt32 LogMaxSize,
     UInt32 LogMaxHistory,
     Boolean DebugLogging
);
```

#### Parameters

`LogLevel` Data type: `UInt32`

Qualifiers: \[in\]

The level of detail that the log will capture. Possible values are shown below. The default value is 1.

| Value | Description |
| --- | --- |
| 0 | Verbose logging |
| 1 | Normal logging |
| 2 | No logging |

`LogMaxSize` Data type: `UInt32`

Qualifiers: \[in\]

The maximum size, in bytes, of a given log file.

`LogMaxHistory` Data type: `UInt32`

Qualifiers: \[in\]

The number of incremented log files to accumulate before deleting. When this number has been reached, the creation of a new log file results in the deletion of the oldest existing log file.

`DebugLogging` Data type: `Boolean`

Qualifiers: \[in\]

`true` if debug logging should be enabled. Debug logging is rarely used except for troubleshooting.

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Remarks

This method manipulates registry keys. These keys shouldn't be manipulated directly. However, for reference, these keys can be found at HKEY\_LOCAL\_MACHINE/Software/Microsoft/CCM/logging/@GLOBAL. Enabling debug logging with `DebugLogging` results in the creation of a new key: HKEY\_LOCAL\_MACHINE/Software/Microsoft/CCM/logging/debuglogging.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[SMS\_Client Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class) [EvaluateMachinePolicy method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/evaluatemachinepolicy-method-in-class-sms_client) [GetAssignedSite method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/getassignedsite-method-in-class-sms_client) [RequestMachinePolicy method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/requestmachinepolicy-method-in-class-sms_client) [ResetPolicy method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/resetpolicy-method-in-class-sms_client) [SetAssignedSite method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setassignedsite-method-in-class-sms_client) [TriggerSchedule method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/triggerschedule-method-in-class-sms_client)
