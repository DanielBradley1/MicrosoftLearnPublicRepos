<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategorycount-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICIINFO::GetCategoryCount Method

The `ICIINFO::GetCategoryCount` method, in Configuration Manager, gets the count of categories that are associated with the configuration item.

## Syntax

```
[IDL]
HRESULT GetCategoryCount(
     ULONG* pulCount
);
```

#### Parameters

`pulCount` Data type: `ULONG`

Qualifiers: \[out\]

Pointer to the count of categories applied to the configuration item.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface)
