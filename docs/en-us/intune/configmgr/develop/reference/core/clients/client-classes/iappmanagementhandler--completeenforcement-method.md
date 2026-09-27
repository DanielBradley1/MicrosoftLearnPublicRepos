<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--completeenforcement-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IAppManagementHandler::CompleteEnforcement Method

The `IAppManagementHandler::CompleteEnforcement` method, in Configuration Manager, completes the installation of a specific application. This method will be called only when the handler returned valid reconnection data in the EnforceApp call.

## Syntax

```
[IDL]
HRESULT CompleteEnforcement(
     AppAction eEnforceAction,
     IWbemClassObject* pHandlerSynclet,
     IWbemClassObject* pReconnectData,
     HANDLE hInstallProcess,
     DWORD* pdwExitCode,
     LPWSTR* ppszExecutionStatus
);
```

#### Parameters

`eEnforceAction` Data type: `AppAction`

Qualifiers: \[in\]

.

`pHandlerSynclet` Data type: `IWbemClassObject`

Qualifiers: \[in\]

.

`pReconnectData` Data type: `IWbemClassObject`

Qualifiers: \[in\]

.

`hInstallProcess` Data type: `HANDLE`

Qualifiers: \[in\]

.

`pdwExitCode` Data type: `DWORD`

Qualifiers: \[out\]

.

`ppszExecutionStatus` Data type: `LPWSTR`

Qualifiers: \[out\]

.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Application Management Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/application-management-client-interfaces) [Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
