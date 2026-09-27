<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/storeevent-method-in-class-ccm_clientevents -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# StoreEvent Method in Class CCM\_ClientEvents

The `StoreEvent` Windows Management Instrumentation \(WMI\) class method generates store events.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```

 uint32 StoreEvent
{
     UInt32 DurationMS,
     String ComponentName,
     String EventName,
     String SessionId
 };
```

## Parameters

`DurationMS` Data type: `UInt32`

Qualifiers: \[in\]

The duration of the event in milliseconds.

`ComponentName` Data type: `String`

Qualifiers: \[in\]

The name of the component.

`EventName` Data type: `String`

Qualifiers: \[in\]

The name of the event.

`SessionId` Data type: `String`

Qualifiers: \[in\]

The ID of the session.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[CCM\_ClientEvents Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_clientevents-client-wmi-class)
