<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/queuerequestedapppolicy-method-in-class-ccm_requestedapppolicy -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# QueueRequestedAppPolicy Method in Class CCM\_RequestedAppPolicy

The `QueueRequestedAppPolicy` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that queues and application policy request.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 QueueRequestedAppPolicy
{
    [IN]    String PolicyId
    [IN]    String PolicyRevision
    [IN]    String Id
    [IN]    UInt32 EnforcePreference
};
```

## Parameters

`PolicyId` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Policy identifier.

`PolicyRevision` Data type: `String`

Qualifiers: \[id\("1"\), in\]

Policy revision.

`Id` Data type: `String`

Qualifiers: \[id\("2"\), in\]

Identifier.

`EnforcePreference` Data type: `UInt32`

Qualifiers: \[id\("3"\), in\]

Enforce preference. Possible values are:

| Value | Enforce preference |
| --- | --- |
| 0 | Immediate |
| 1 | Non-Business Hours |
| 2 | Admin Schedule |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
