<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_requested-apppolicy-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Requested AppPolicy Client WMI Class

The `CCM_RequestedAppPolicy` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents an application policy request.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_RequestedAppPolicy :
{
    String AppId;
    DateTime DateRequested;
    UInt32 EnforcePreference;
    Boolean IsComplete;
    Boolean IsRebootIfNeeded;
    Boolean IsSlowInstallRequest;
    String PolicyId;
    UInt32 RequestedActions;
    String Revision;
    String UserSID;
};
```

## Methods

The following table lists the methods in the `CCM_RequestedAppPolicy` class.

- [QueueRequestedAppPolicy Method in Class CCM\_RequestedAppPolicy](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/queuerequestedapppolicy-method-in-class-ccm_requestedapppolicy)

## Properties

`AppId` Data type: `String`

Access type: Read/Write

Qualifiers: none

Application identifier.

`DateRequested` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

Date requested.

`EnforcePreference` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[values\]

Enforce preference. Possible values are:

| Value | Enforce preference |
| --- | --- |
| 0 | Immediate |
| 1 | Non-business Hours |
| 2 | Admin Schedule |

`IsComplete` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if application request is complete.

`IsRebootIfNeeded` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if a reboot is needed.

`IsSlowInstallRequest` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this is an installation over a slow link.

`PolicyId` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Policy identifier.

`RequestedActions` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Requested actions.

`Revision` Data type: `String`

Access type: Read/Write

Qualifiers: none

Revision.

`UserSID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

User security identifier \(SID\).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
