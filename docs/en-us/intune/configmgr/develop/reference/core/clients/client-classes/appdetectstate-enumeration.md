<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/appdetectstate-enumeration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AppDetectState Enumeration

In Configuration Manager, the `AppDetectState` enumeration defines application installation states. This enumeration is used by the [IAppManagementHandler Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler-interface).

## Syntax

```
typedef enum tagAppDetectState
{
    appDetectNotFound = 0,
    appDetectInstalled,
    appDetectFailed
}AppDetectState;
```

## Elements

`appDetectNotFound` The application was not found.

`appDetectInstalled` The application is installed.

`appDetectFailed` Application detection failed.

## Remarks

This enumeration is used by the [IAppManagementHandler Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementhandler-interface).

## See Also

[Application Management Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/application-management-client-interfaces) [Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
