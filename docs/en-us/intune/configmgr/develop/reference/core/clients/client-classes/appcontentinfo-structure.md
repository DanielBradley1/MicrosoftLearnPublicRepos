<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/appcontentinfo-structure -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AppContentInfo Structure

In Configuration Manager, the `AppContentInfo` structure contains information about the application content.

## Syntax

```
struct AppContentInfo
{
    LPCWSTR szContentId;
    LPCWSTR szContentVersion;
    LPCWSTR szLocalPath;
};
```

## Members

`szContentId` The content id.

`szContentVersion` The content version.

`szLocalPath` The local path.

## See Also

[Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
