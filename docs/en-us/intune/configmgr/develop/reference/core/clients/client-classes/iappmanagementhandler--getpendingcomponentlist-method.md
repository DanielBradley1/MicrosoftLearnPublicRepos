<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler--getpendingcomponentlist-method -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# IAppManagementHandler::GetPendingComponentList Method

The `IAppManagementHandler::GetPendingComponentList` method, in Configuration Manager, gets the pending component list for a specified deployment type. This is an optional method for the application deployment type handler. It's called if the handler returns a status of "PendingUpdate" for the `EnforceApp` method. Software Center presents a list of these components to the end user, which need to be closed in order for the `EnforceApp` method to succeed.

## Syntax

```
[IDL]
HRESULT GetPendingComponentList(
     IWbemClassObject* pDeliveryTypeSynclet,
     LPWSTR* pwszPendingComponentList
);
```

#### Parameters

`pDeliveryTypeSynclet` Data type: `IWbemClassObject`

Qualifiers: \[in\]

The WMI object for the installation synclet which is associated with the application deployment type that is being installed.

`pwszPendingComponentList` Data type: `LPWSTR`

Qualifiers: \[out\]

The pending component list in XML format.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

E\_NOTIMPL The method isn't supported by the handler.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
