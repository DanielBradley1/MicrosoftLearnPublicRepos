<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/resetpolicy-method-in-class-sms_client -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ResetPolicy Method in Class SMS\_Client

In Configuration Manager, the `ResetPolicy` method, resets the policy on a client. As a result, the next policy request will receive a full policy instead of merely the change in policy since the last policy request.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 ResetPolicy(
     UInt32 uFlags
);
```

#### Parameters

`uFlags` Data type: `UInt32`

Qualifiers: \[in\]

Flags identifying the policy. Possible values are:

| Value | Description |
| --- | --- |
| 0 | The next policy request will be for a full policy instead of the change in policy since the last policy request. |
| 1 | The existing policy will be purged completely. |

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Remarks

Indiscriminate calling of this method could have adverse effects. For example, if you purge the existing policy \(`ulFlags` = 1\) software distribution programs could be run more than once. If the request is for full policy \(`ulFlags` = 0\), you could generate unnecessary network traffic.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[SMS\_Client Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class) [EvaluateMachinePolicy method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/evaluatemachinepolicy-method-in-class-sms_client) [GetAssignedSite method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/getassignedsite-method-in-class-sms_client) [RequestMachinePolicy method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/requestmachinepolicy-method-in-class-sms_client) [SetAssignedSite method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setassignedsite-method-in-class-sms_client) [SetGlobalLoggingConfiguration method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setgloballoggingconfiguration-method-in-class-sms_client) [TriggerSchedule method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/triggerschedule-method-in-class-sms_client)
