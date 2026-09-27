<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler-interface -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IAppManagementHandler Interface

The `IAppManagementHandler` interface, in Configuration Manager defines functions to interact with the handler.

The interface inherits from `IUnknown`.

## In This Section

The following table lists the methods in the `IAppManagementHandler` interface.

| Term | Definition |
| --- | --- |
| [IAppManagementHandler::CheckReconnectData Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--checkreconnectdata-method) | The `IAppManagementHandler::CheckReconnectData` method, in Configuration Manager, checks whether the reconnection data is valid. |
| [IAppManagementHandler::CompleteEnforcement Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--completeenforcement-method) | The `IAppManagementHandler::CompleteEnforcement` method, in Configuration Manager, completes the installation of a specific application. This method will be called only when the handler returned valid reconnection data in the EnforceApp call. |
| [IAppManagementHandler::DiscoverApp Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--discoverapp-method) | The `IAppManagementHandler::DiscoverApp` method, in Configuration Manager, runs a synchronous discovery operation for the provided synclet. |
| [IAppManagementHandler::EnforceApp Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enforceapp-method) | The `IAppManagementHandler::EnforceApp` method, in Configuration Manager, starts the installation of a specific application. |
| [IAppManagementHandler::EnumerateApps Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enumerateapps-method) | The `IAppManagementHandler::EnumerateApps` method, in Configuration Manager, runs a synchronous discovery operation for the provided synclet. |
| [IAppManagementHandler::GetPendingComponentList Function](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--getpendingcomponentlist-method) | The `IAppManagementHandler::GetPendingComponentList` method, in Configuration Manager, gets the pending component list for a specified deployment type. |

## Remarks

To obtain this interface, the application calls the `IAppManagementHandler` interface.

## UUID

The UUID for `IAppManagementHandler` is B206D835-6BD3-4e70-952E-FBA99AEBC5CE.

## See Also

[Application Management Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/application-management-client-interfaces) [Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
