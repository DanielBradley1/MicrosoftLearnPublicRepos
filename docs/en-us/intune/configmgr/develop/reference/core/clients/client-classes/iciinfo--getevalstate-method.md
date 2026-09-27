<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getevalstate-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICIINFO::GetEvalState Method

The `ICIINFO::GetEvalState` method, in Configuration Manager, gets the current evaluation state of the configuration item.

## Syntax

```
[IDL]
HRESULT GetEvalState(
     CIEvalState* pCIEvalState
);
```

#### Parameters

`pCIEvalState` Data type: `CIEvalState`

Qualifiers: \[out\]

Pointer to a [CIEvalState Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cievalstate-enumeration) value indicating the evaluation state.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface) [CIEvalState Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cievalstate-enumeration)
