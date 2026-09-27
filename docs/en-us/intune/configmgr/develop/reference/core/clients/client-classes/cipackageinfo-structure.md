<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cipackageinfo-structure -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CIPackageInfo Structure

In Configuration Manager, the `CIPackageInfo` structure contains package information for a configuration item.

## Syntax

```
struct CIPackageInfo
{
      LPWSTR szTypeName;
      LPWSTR szPackageName;
      LPWSTR szPackageVersion;
      LPWSTR szNamespace;
};
```

## Members

szTypeName Name of the configuration item.

szPackageName Name of the package.

szPackageVersion Version of the package.

szNamespace Namespace used by the package software.

## See Also

[Compliance Settings \(DCM\) Client Interfaces](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/compliance-settings--dcm--client-interfaces) [ICIINFO::GetDependantPackages Method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdependantpackages-method)
