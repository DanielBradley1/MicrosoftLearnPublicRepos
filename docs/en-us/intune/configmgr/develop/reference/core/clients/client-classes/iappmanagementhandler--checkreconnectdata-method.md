<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--checkreconnectdata-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IAppManagementHandler::CheckReconnectData Method

The `IAppManagementHandler::CheckReconnectData` method, in Configuration Manager, checks whether the reconnection data is valid.

## Syntax

```
[IDL]
HRESULT CheckReconnectData(
     IWbemClassObject* pReconnectData,
     BOOL* pfIsValid,
     BOOL* pfEnforcementFinished
);
```

#### Parameters

`pReconnectData` Data type: `IWbemClassObject`

Qualifiers: \[in\]

.

`pfIsValid` Data type: `BOOL`

Qualifiers: \[out\]

.

`pfEnforcementFinished` Data type: `BOOL`

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

[Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
