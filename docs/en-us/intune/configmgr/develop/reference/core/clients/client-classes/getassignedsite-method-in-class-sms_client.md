<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/getassignedsite-method-in-class-sms_client -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetAssignedSite Method in Class SMS\_Client

In Configuration Manager, the `GetAssignedSite` method gets the current assigned site of the client.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 GetAssignedSite(
     String sSiteCode
);
```

#### Parameters

`sSiteCode` Data type: `String`

Qualifiers: \[out\]

The site code for the currently assigned site.

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[SMS\_Client Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class) [EvaluateMachinePolicy method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/evaluatemachinepolicy-method-in-class-sms_client) [RequestMachinePolicy method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/requestmachinepolicy-method-in-class-sms_client) [ResetPolicy method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/resetpolicy-method-in-class-sms_client) [SetAssignedSite method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setassignedsite-method-in-class-sms_client) [SetGlobalLoggingConfiguration method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setgloballoggingconfiguration-method-in-class-sms_client) [TriggerSchedule method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/triggerschedule-method-in-class-sms_client)
