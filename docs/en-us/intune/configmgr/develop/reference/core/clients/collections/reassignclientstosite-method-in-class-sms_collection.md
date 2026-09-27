<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/reassignclientstosite-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ReassignClientsToSite Method in Class SMS\_Collection

The `ReassignClientsToSite` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, reassigns the Configuration Manager site for clients in the list.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ReassignClientsToSite(
     UInt32 ResourceIDs[],
     Boolean NewSiteCode
     SInt32 ReturnValue
);
```

#### Parameters

`ResourceIDs` Data type: `UInt32` Array

Qualifiers: \[in\]

IDs of member resources.

`NewSiteCode` Data type: `String`

Qualifiers: \[in\]

The new site code for the clients.

`ReturnValue` Data type: `SInt32`

Qualifiers: \[out\]

The number of devices that were successfully reassigned.

Important

Even if there is an error, some devices may still get reassigned.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
