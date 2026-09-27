<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--rawevent-property -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# ICCMEvent::RawEvent Property

`ICcmEvent::RawEvent` is a read-only property in Configuration Manager that indicates information to add to a raw event.

## Syntax

```
[C++]
HRESULT ICcmEvent::RawEvent([out, retval] IUnknown** ppWmiEvent);
```

#### Parameters

`ppWmiEvent` Data type: `IUnknown`

Qualifiers: \[out, retval\]

Pointer to a pointer to the `IUnknown` interface of the internal Windows Management Instrumentation \(WMI\) event.

## Return Values

The property returns an `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded.

## Remarks

Use of this property permits information that can't be added through the [SetProperty method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--setproperty-method) method to be added to custom events.

This property is recommended only for advanced users who need to add information to custom events that can't be accomplished through the [SetProperty method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--setproperty-method) method. It isn't supported in VBScript.

## Requirements

Smscore.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[SMSEvent Class \(client\)](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smsevent-class)
