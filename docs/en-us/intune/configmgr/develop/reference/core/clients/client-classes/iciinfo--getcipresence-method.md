<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcipresence-method -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# ICIINFO::GetCIPresence Method

The `ICIINFO::GetCIPresence` method, in Configuration Manager, gets the current presence for the configuration item. The presence data includes the compliance state for the configuration item.

## Syntax

```
[IDL]
HRESULT GetCIPresence(
     CIPresence* pCIPresence
);
```

#### Parameters

`pCIPresence` Data type: `CIPresence`

Qualifiers: \[out\]

Pointer to a [CIPresence Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cipresence-enumeration) value indicating the current presence for the configuration item.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface) [CIPresence Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cipresence-enumeration)
