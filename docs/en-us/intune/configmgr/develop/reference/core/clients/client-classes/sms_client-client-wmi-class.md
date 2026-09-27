<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_Client Client WMI Class

The `SMS_Client` class is a client Windows Management Instrumentation \(WMI\) class, in Configuration Manager, that represents the client and facilitates manipulation and retrieval of client information.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```syntax
Class SMS_Client
{
      Boolean AllowLocalAdminOverride;
      UInt32 ClientType;
      String ClientVersion;
      Boolean EnableAutoAssignment;
};
```

## Methods

The following table shows the methods in `SMS_Client`.

| Method | Description |
| --- | --- |
| [EvaluateMachinePolicy Method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/evaluatemachinepolicy-method-in-class-sms_client) | Initiates the evaluation of the policy assigned to a specified computer or device. |
| [GetAssignedSite Method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/getassignedsite-method-in-class-sms_client) | Gets the current assigned site of the client. |
| [RequestMachinePolicy Method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/requestmachinepolicy-method-in-class-sms_client) | Initiates a request for machine policy. |
| [ResetPolicy Method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/resetpolicy-method-in-class-sms_client) | Resets the policy on a client. |
| [SetAssignedSite Method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setassignedsite-method-in-class-sms_client) | Sets the client's assigned site. |
| **SetClientProvisioningMode** | Reserved. |
| [SetGlobalLoggingConfiguration Method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/setgloballoggingconfiguration-method-in-class-sms_client) | Defines the default logging configuration. |
| [TriggerSchedule Method in Class SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/triggerschedule-method-in-class-sms_client) | Triggers the client to execute the specified schedule. |

## Properties

### `AllowLocalAdminOverride`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

Reserved.

### `ClientType`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Reserved. Always 1.

### `ClientVersion`

Data type: `String`

Access type: Read/Write

Qualifiers: None

Version number of the client.

### `EnableAutoAssignment`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

`true` if automatic assignment is enabled.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Client Framework and Data Transfer Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/client-framework-and-data-transfer-client-wmi-classes)
