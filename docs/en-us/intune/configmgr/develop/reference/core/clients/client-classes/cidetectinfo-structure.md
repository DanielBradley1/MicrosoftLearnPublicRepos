<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cidetectinfo-structure -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CIDetectInfo Structure

In Configuration Manager, the `CIDetectInfo` structure contains identity information for baseline configuration item detection.

## Syntax

```
struct CIDetectInfo
{
      LPWSTR szCIID;
      LPWSTR szVersion;
};
```

## Members

szCIID ID of the configuration item.

szVersion Version of the configuration item.

## See Also

[Compliance Settings \(DCM\) Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/compliance-settings--dcm--client-interfaces)
