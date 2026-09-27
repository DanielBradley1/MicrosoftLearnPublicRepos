<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getlastevaltime-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICIINFO::GetLastEvalTime Method

The `ICIINFO::GetLastEvalTime` method, in Configuration Manager, gets the last evaluation time for the configuration item.

## Syntax

```
[IDL]
HRESULT GetLastEvalTime(
     SYSTEMTIME* pstEvalTime
);
```

#### Parameters

`pstEvalTime` Data type: `SYSTEMTIME`

Qualifiers: \[out\]

Pointer to a `SYSTEMTIME` object indicating the last evaluation time.

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
