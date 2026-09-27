<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/start-method-in-class-sms_azureservice -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Start method in class SMS\_AzureService

The `Start` WMI class method in Configuration Manager that's invoked to start a Microsoft Azure service that represents a cloud distribution point for Configuration Manager.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 Start
{
    [IN]    UInt32 AzureServiceID
};
```

## Parameters

`AzureServiceID` Data type: `UInt32`

Qualifiers: \[id\("0"\), in\]

The service identifier key for the `SMS_AzureService` instance on which the current task will be performed.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
