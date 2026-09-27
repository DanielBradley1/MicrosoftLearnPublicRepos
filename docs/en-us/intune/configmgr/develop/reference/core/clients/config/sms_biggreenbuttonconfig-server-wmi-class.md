<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_biggreenbuttonconfig-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# SMS\_BigGreenButtonConfig Server WMI Class

The `SMS_BigGreenButtonConfig` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that can stop clients from connecting to the client notification server \(a hidden role, co-located with management point\).

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_BigGreenButtonConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    Boolean EnableClientNotification;
};
```

## Methods

The `SMS_BigGreenButtonConfig` class doesn't define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, read\]

Identifies the client agent component. The BigGreenButton Agent ID is 18.

`EnableClientNotification` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`false` to stop clients from connecting to the client notification server \(a hidden role, co-located with management point\). No active connections are established between the clients and the client notification server. The default value is `true`.

This setting is part of the client infrastructure and turned on by default. This value would likely only be changed to troubleshoot a significant performance issue.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
