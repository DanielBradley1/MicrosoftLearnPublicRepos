<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback-interface -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IDCMAgentCallback Interface

The `IDCMAgentCallback` interface, in Configuration Manager, represents the callback for the Desired Configuration Management Agent. This interface inherits from `IUnknown`.

## In This Section

The following table lists the methods in the `IDCMAgentCallback` interface.

| Term | Definition |
| --- | --- |
| [IDCMAgentCallback::NotifyComplete](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifycomplete-method) | Notifies the caller that a Desired Configuration Management agent job has been completed. |
| [IDCMAgentCallback::NotifyError](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyerror-method) | Notifies the caller that a Desired Configuration Management agent job has failed to be completed. |
| [IDCMAgentCallback::NotifyProgress](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmagentcallback--notifyprogress-method) | Notifies the caller of progress made on a Desired Configuration Management agent job. |

## UUID

The UUID for `IDCMAgentCallback` is 513FB8A1-67E9-4f18-8E77-0CBD6BE95708.

## See Also

[Compliance Settings \(DCM\) Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/compliance-settings--dcm--client-interfaces)
