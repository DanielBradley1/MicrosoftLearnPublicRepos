<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_requestedapppolicyactivation-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_RequestedAppPolicyActivation Client WMI Class

The `CCM_RequestedAppPolicyActivation` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a requested application policy activation.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_RequestedAppPolicyActivation :
{
    UInt32 ActivationAction;
    String AppId;
    DateTime DateRequested;
    Boolean IsComplete;
    String PolicyId;
    String Revision;
    String UserSID;
};
```

## Methods

The following table lists the methods in the `CCM_RequestedAppPolicyActivation` class.

- [QueueAppPolicyActivationAction Method in Class CCM\_RequestedAppPolicyActivation](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/queueapppolicyactivationaction-method-in-class-ccm_requestedapppolicyactivation)

## Properties

`ActivationAction` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[values\]

Activation action. Possible values are:

| Value | Activation action |
| --- | --- |
| 0 | default |
| 1 | By-pass Activation |

`AppId` Data type: `String`

Access type: Read/Write

Qualifiers: none

Application identifier.

`DateRequested` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Date requested.

`IsComplete` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if activation is complete.

`PolicyId` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Policy identifier.

`Revision` Data type: `String`

Access type: Read/Write

Qualifiers: none

Application revision.

`UserSID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

User security identifier \(SID\).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
