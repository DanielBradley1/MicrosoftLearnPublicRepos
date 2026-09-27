<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/requestmachinepolicy-method-in-class-sms_client -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# RequestMachinePolicy Method in Class SMS\_Client

The `RequestMachinePolicy` method, in Configuration Manager, initiates a request for machine policy.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 RequestMachinePolicy(
      UInt32 uFlags
);
```

#### Parameters

`uFlags` Data type: `UInt32`

Qualifiers: \[in\]

Flags identifying the policy. Possible values are:

| Value | Description |
| --- | --- |
| 0 | A machine policy retrieval cycle is initiated. |
| 1 | A machine policy validation cycle is initiated, and the server and client cyclical redundancy checks \(CRCs\) are compared to verify that the policies are in agreement. If the policies aren't in agreement, then a resynchronization is initiated. |

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[SMS\_Client Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class) [EvaluateMachinePolicy method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/evaluatemachinepolicy-method-in-class-sms_client) [GetAssignedSite method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/getassignedsite-method-in-class-sms_client) [ResetPolicy method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/resetpolicy-method-in-class-sms_client) [SetAssignedSite method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setassignedsite-method-in-class-sms_client) [SetGlobalLoggingConfiguration method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setgloballoggingconfiguration-method-in-class-sms_client) [TriggerSchedule method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/triggerschedule-method-in-class-sms_client)
