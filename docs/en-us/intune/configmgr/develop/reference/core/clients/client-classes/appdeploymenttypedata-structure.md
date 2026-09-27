<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/appdeploymenttypedata-structure -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AppDeploymentTypeData Structure

In Configuration Manager, the `AppDeploymentTypeData` structure contains detection results for a set of deployment types.

## Syntax

```
typedef struct tagAppDeploymentTypeData
{
    DWORD cbSize;
    DWORD dwCount;
    PAppDeploymentTypeItem pData;
}AppDeploymentTypeData;
```

## Members

`cbSize` The size of this structure to indicate version.

`dwCount` The number of discovered items.

`PAppDeploymentTypeItem` An array of discovered items.

## See Also

[Application Management Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/application-management-client-interfaces) [Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
