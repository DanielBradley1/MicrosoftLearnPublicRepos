<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--submit-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICCMEvent::Submit Method

In Configuration Manager, the `ICcmEvent::Submit` method submits an event to Windows Management Instrumentation \(WMI\).

## Syntax

```
[C++]
HRESULT ICcmEvent::Submit();
```

#### Parameters

None.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded.

## Requirements

Smscore.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[SMSEvent Class \(client\)](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smsevent-class)
