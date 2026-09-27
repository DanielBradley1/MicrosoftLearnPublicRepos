<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getid-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICIINFO::GetId Method

The `ICIINFO::GetId` method, in Configuration Manager, gets the ID of the configuration item.

## Syntax

```
[IDL]
HRESULT GetId(
    LPWSTR* ppszId
);
```

#### Parameters

`ppszId` Data type: `LPWSTR`

Qualifiers: \[out\]

Pointer to the ID of the configuration item.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface)
