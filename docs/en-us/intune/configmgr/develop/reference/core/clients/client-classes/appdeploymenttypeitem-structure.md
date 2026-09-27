<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/appdeploymenttypeitem-structure -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AppDeploymentTypeItem Structure

In Configuration Manager, the `AppDeploymentTypeItem` structure contains detection results for an individual deployment type.

## Syntax

```
typedef struct tagAppDeploymentTypeItem
{
    LPWSTR szId;
    DWORD dwRevision;
    AppDetectState eDetectState;
    DWORD dwErrorCode;
}AppDeploymentTypeItem, *PAppDeploymentTypeItem;
```

## Members

`szId` ID of the deployment item.

`dwRevision` Revision.

`eDetectState` Detect state.

dwErrorCode Error code.

## See Also

[Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
