<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/config/sms_statesystemconfig-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_StateSystemConfig Server WMI Class

The `SMS_StateSystemConfig` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that specifies how client computers report state messages.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_StateSystemConfig : SMS_ClientAgentConfig_BaseClass
{
    UInt32 AgentID;
    UInt32 BulkSendInterval;
    UInt32 BulkSendIntervalHigh;
    UInt32 BulkSendIntervalLow;
    String CacheCleanoutInterval;
    UInt32 CacheMaxAge;
};
```

## Methods

The `SMS_StateSystemConfig` class does not define any methods.

## Properties

`AgentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key, read\]

Identifies the client agent component. The State System Config Agent ID is 16.

`BulkSendInterval` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reporting cycle, in minutes, for state messages with normal priority.

`BulkSendIntervalHigh` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reporting cycle, in minutes, for state messages with high priority.

`BulkSendIntervalLow` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reporting cycle, in minutes, for state messages with low priority.

`CacheCleanoutInterval` Data type: `String`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

`CacheMaxAge` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Reserved for future use.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
