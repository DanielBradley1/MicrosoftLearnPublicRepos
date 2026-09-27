<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--enumerateapps-method -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# IAppManagementHandler::EnumerateApps Method

The `IAppManagementHandler::EnumerateApps` method, in Configuration Manager, runs a synchronous discovery operation for the provided synclet.

## Syntax

```
[IDL]
HRESULT EnumerateApps(
     HANDLE hUserToken,
     AppDeploymentTypeData* pDetectResult
);
```

#### Parameters

`hUserToken` Data type: `HANDLE`

Qualifiers: \[in\]

The user token. If it's null, the action is for computer. If it isn't NULL, the action is for the user.

`pDetectResult` Data type: `AppDeploymentTypeData`

Qualifiers: \[out\]

.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Success implies that discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[IAppManagementHandler Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler-interface) [Application Management Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/application-management-client-interfaces) [Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
