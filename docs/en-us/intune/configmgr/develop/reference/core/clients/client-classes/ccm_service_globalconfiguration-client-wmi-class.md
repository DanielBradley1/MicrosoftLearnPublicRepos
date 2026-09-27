<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_service_globalconfiguration-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_Service\_GlobalConfiguration Client WMI Class

In Configuration Manager, the `CCM_Service_GlobalConfiguration` class is a client Windows Management Instrumentation \(WMI\) class that supports global configuration for the CCMEXEC service. There's only one instance of this class on a computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class CCM_Service_GlobalConfiguration : CCM_Policy
{
      UInt8 Dummy;
      UInt32 EndpointActiveMessageThreshold;
      UInt32 EndpointMessageTimeout;
      UInt32 EndpointReleaseTimeout;
      UInt32 OutgoingMessageTimeout;
      String PolicyID;
      String PolicyInstanceID;
      UInt32 PolicyPrecedence;
      String PolicyRuleID;
      String PolicySource;
      String PolicyVersion;
      String ServiceRootDir;
};
```

## Methods

The `CCM_Service_GlobalConfiguration` class doesn't define any methods.

## Properties

`Dummy` Data type: `UInt8`

Access type: Read/Write

Qualifiers: \[Realkey\]

Dummy key.

`EndpointActiveMessageThreshold` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Default maximum number of outstanding messages that endpoints are allowed. A message is outstanding if it has been dispatched to the endpoint, but the endpoint hasn't called **SetComplete** on the associated context. For serial endpoints, the AMT is always 1. This can be overridden on a per-endpoint basis.

`EndpointMessageTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Default timeout, in minutes, assigned to all messages that arrive for endpoints. If the value is NULL or 0, no default timeout is assigned. This can be overridden on a per-endpoint basis.

`EndpointReleaseTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Endpoint defaults. The default idle time, in minutes, that endpoints are allowed before they're released by the service. An endpoint is idle when no messages are being dispatched to it. If the value is NULL or 0, endpoints aren't released until the service shuts down. This can be overridden on a per-endpoint basis in the endpoint's configuration.

`OutgoingMessageTimeout` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Service defaults. The default timeout, in minutes, that all messages sent from the computer are assigned. If the value is NULL or 0, no default timeout is assigned. This can be overridden on a per-message basis by using the **Timeout** property of the message.

`PolicyID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`PolicyInstanceID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`PolicyPrecedence` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`PolicyRuleID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`PolicySource` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`PolicyVersion` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [CCM\_Policy Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/ccm_policy-client-wmi-class).

`ServiceRootDir` Data type: `String`

Access type: Read/Write

Qualifiers: None

Root directory that the service uses internally for temporary files. The System and Administrators account must have full access to this directory \(the latter is to allow the debugging of CCMEXEC as an application\). The service creates this directory if it doesn't exist.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Client Framework and Data Transfer Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/client-framework-and-data-transfer-client-wmi-classes)
