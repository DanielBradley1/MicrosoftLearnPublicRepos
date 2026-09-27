<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getsdmtypename-method -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# ICIINFO::GetSdmTypeName Method

The `ICIINFO::GetSdmTypeName` method, in Configuration Manager, gets the fully qualified name of a configuration item.

## Syntax

```
[IDL]
HRESULT GetSdmTypeName(
     LPWSTR* ppszTypeName
);
```

#### Parameters

`ppszTypeName` Data type: `LPWSTR`

Qualifiers: \[out\]

Pointer to a string that represents the fully qualified name of the configuration item.

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
