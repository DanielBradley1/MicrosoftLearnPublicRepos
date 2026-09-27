<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/appaction-enumeration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AppAction Enumeration

In Configuration Manager, the `AppAction` enumeration defines action types. This enumeration is used by the [IAppManagmentTypes Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementtypes-interface).

## Syntax

```
typedef enum AppAction
{
    appDiscovery = 0,
    appInstall = 1,
    appUninstall = 2
}AppAction;
```

## Elements

`appDiscovery` The action type is discovery.

`appInstall` The action type is install.

`appUninstall` The action type is uninstall.

## See Also

[IAppManagementTypes Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappmanagementtypes-interface) [Application Management Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/application-management-client-interfaces) [Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
