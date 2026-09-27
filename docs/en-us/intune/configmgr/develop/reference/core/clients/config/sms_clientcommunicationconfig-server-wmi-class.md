<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_clientcommunicationconfig-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# SMS\_ClientCommunicationConfig Server WMI Class

The `SMS_ClientCommunicationConfig` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that controls how Windows 8 client computers communicate with Configuration Manager sites when they use metered Internet connections.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ClientCommunicationConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    UInt32 MeteredNetworkUsage;
};
```

## Methods

The `SMS_ClientCommunicationConfig` class doesn't define any methods.

## Properties

`MeteredNetworkUsage` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Set metered network usage behavior. Possible values are:

| Value | Metered network usage policy |
| --- | --- |
| 1 | Allow metered network use. |
| 2 | Only use the metered network for deployments that are marked to allow use of the metered network. This means meta-data such as policy will always use the metered network. And based on the policy, the client decides whether or not to use the metered network for the deployment. |
| 4 | Block metered network usage. |

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
