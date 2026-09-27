<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--eventtype-property -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# ICCMEvent::EventType Property

`ICcmEvent::EventType` is a read/write property in Configuration Manager that indicates the type of Windows Management Instrumentation \(WMI\) event that is being raised.

## Syntax

```
[C++]
HRESULT ICcmEvent::EventType([out, retval] BSTR* sEventType);

HRESULT ICcmEvent::EventType([in] BSTR sEventType);
```

#### Parameters

`sEventType` Data type: `BSTR`

Qualifiers: \[in, out, retval\]

On input, the value to set for the event type. On output, this parameter points to the retrieved event type.

## Return Values

The property returns an `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded.

## Remarks

This property must correspond to an `ICcmEvent`-derived class registered in the root\\ccm\\events namespace.

## Requirements

Smscore.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[SMSEvent Class \(client\)](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smsevent-class)
