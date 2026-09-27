<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_clientresourcesconfig-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ClientResourcesConfig Server WMI Class

The `SMS_ClientResourcesConfig` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the settings and properties used by the client agent.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientResourcesConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    Boolean DisableGlobalRandomization;
};
```

## Methods

The `SMS_ClientResourcesConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, read\]

Identifies the client agent component. The SMS\_ClientResourcesConfig Agent ID is 25.

`DisableGlobalRandomization` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` disables global randomization.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
