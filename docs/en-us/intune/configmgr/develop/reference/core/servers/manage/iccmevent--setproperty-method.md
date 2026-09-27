<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--setproperty-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICCMEvent::SetProperty Method

In Configuration Manager, the `ICcmEvent::SetProperty` method sets an event property.

## Syntax

```
[C++]
HRESULT ICcmEvent::SetProperty
(
      BSTR sPropName,
   VARIANT* vPropValue
);
```

#### Parameters

`sPropName` Data type: `BSTR`

Qualifiers: \[in\]

Name of the property to set. This must correspond to a property name in the Windows Management Instrumentation \(WMI\) event class.

`vPropValue` Data type: `VARIANT`

Qualifiers: \[in\]

Pointer to the new value for the property.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded.

## Remarks

Your application must set the [EventType property](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--eventtype-property) before calling this method.

## Requirements

Smscore.dll.

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[SMSEvent Class \(client\)](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smsevent-class)
