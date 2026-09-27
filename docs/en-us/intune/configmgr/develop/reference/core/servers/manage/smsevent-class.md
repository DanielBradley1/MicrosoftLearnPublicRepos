<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/smsevent-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMSEvent Class

The `SmsEvent` class represents a Configuration Manager event on the client. The class implements the `ICcmEvent` interface.

## Methods and Properties

| Term | Description |
| --- | --- |
| [ICcmEvent::EventType Property](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--eventtype-property) | Indicates the type of Windows Management Instrumentation \(WMI\) event that is being raised. |
| [ICcmEvent::RawEvent Property](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--rawevent-property) | Adds information to custom events. |
| [ICcmEvent::SetProperty Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--setproperty-method) | Sets an event property. |
| [ICcmEvent::Submit Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--submit-method) | Submits an event to WMI. |
| [ICcmEvent::SubmitPending Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/iccmevent--submitpending-method) | Submits an event to WMI in situations where the Configuration Manager Agent Host \(CCMEXEC\) service might not be running. |

## Remarks

The `ProgID` for the automation object is Microsoft.SMS.Event and it is implemented as part of Smscore.dll. The Visual Basic reference for early binding is SMSCorLib. The early binding object name is `SMSEvent`.

## Requirements

smscore.dll

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
