<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--submitpending-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICCMEvent::SubmitPending Method

In Configuration Manager, the `ICcmEvent::SubmitPending` method submits an event that is stored by Windows Management Instrumentation \(WMI\).

## Syntax

```
[C++]
HRESULT ICcmEvent::SubmitPending(
      BSTR bstrEventID,
      long lFlags
);
```

#### Parameters

`bstrEventID` Data type: `BSTR`

Qualifiers: \[in, optional, defaultvalue\("0"\)\]

Reserved. Must be `null`.

`lFlags` Data type: `long`

Qualifiers: \[in, optional, defaultvalue\(0\)\]

Reserved. Must be zero.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded.

## Remarks

Your application should use this method instead of the [Submit method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--submit-method) in situations where the Configuration Manager Agent Host \(CCMEXEC\) service might not be running. Instead of directly calling CCMEXEC to submit the event, this method stores it in WMI. If the service is running, the event is picked up immediately and issued. Otherwise, it's issued the next time the service starts.

## Requirements

Smscore.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[SMSEvent Class \(client\)](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smsevent-class) [Submit method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--submit-method)
