<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdependantpackages-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICIINFO::GetDependantPackages Method

The `ICIINFO::GetDependantPackages` method, in Configuration Manager, gets the dependent package information for the configuration item.

## Syntax

```
[IDL]
HRESULT GetDependantPackages(
     ULONG* pulNumDependants,
     struct CIPackageInfo** ppInfo
);
```

#### Parameters

`pulNumDependants` Data type: `ULONG`

Qualifiers: \[out\]

Pointer to the number of dependent packages.

`ppInfo` Data type: `CIPackageInfo`

Qualifiers: \[out\]

Pointer to a pointer to one [CIPackageInfo Structure](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cipackageinfo-structure) for each dependent package.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface) [CIPackageInfo Structure](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cipackageinfo-structure)
