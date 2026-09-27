<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enforceapp-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IAppManagementHandler::EnforceApp Method

The `IAppManagementHandler::EnforceApp` method, in Configuration Manager, starts the installation of a specific application.

If the handler supports reconnection, it must return a valid reconnect instance to `ppReconnectData`. If for whatever reason the installation cannot start, but is not in an error state, for example, no user token to display, then the handler should return `S_FALSE`.

## Syntax

```
[IDL]
HRESULT EnforceApp(
     AppAction eEnforceAction,
     HANDLE hUserToken,
     DWORD dwSessionId,
     IWbemClassObject* pHandlerSynclet,
     LPCWSTR szLocalContentPath,
     HANDLE* phInstallProcess,
     DWORD* pdwExitCode,
     LPWSTR* ppszExecutionStatus,
     IWbemClassObject** ppReconnectData
);
```

#### Parameters

`eEnforceAction` Data type: `AppAction`

Qualifiers: \[in\]

.

`hUserToken` Data type: `HANDLE`

Qualifiers: \[in\]

.

`dwSessionId` Data type: `DWORD`

Qualifiers: \[in\]

.

`pHandlerSynclet` Data type: `IWbemClassObject`

Qualifiers: \[in\]

.

`szLocalContentPath` Data type: `LPCWSTR`

Qualifiers: \[in\]

.

`phInstallProcess` Data type: `HANDLE`

Qualifiers: \[out\]

.

`pdwExitCode` Data type: `DWORD`

Qualifiers: \[out\]

.

`ppszExecutionStatus` Data type: `LPWSTR`

Qualifiers: \[out\]

.

`ppReconnectData` Data type: `IWbemClassObject`

Qualifiers: \[out\]

.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure. If for whatever reason the installation cannot start, but is not in an error state, for example, no user token to display UI, then the handler should return `S_FALSE`

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[IAppManagementHandler Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler-interface) [Application Management Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/application-management-client-interfaces) [Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
