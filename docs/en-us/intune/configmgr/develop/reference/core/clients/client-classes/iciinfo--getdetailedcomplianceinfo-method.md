<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getdetailedcomplianceinfo-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICIINFO::GetDetailedComplianceInfo Method

The `ICIINFO::GetDetailedComplianceInfo` method, in Configuration Manager, gets detailed compliance information from the last compliance evaluation run for the configuration item. The string returned by the method contains an XML report from the last evaluation of the configuration item.

## Syntax

```
[IDL]
HRESULT GetDetailedComplianceInfo(
     LPWSTR* ppszComplianceInfo
);
```

#### Parameters

`ppszComplianceInfo` Data type: `LPWSTR`

Qualifiers: \[out\]

Pointer to the detailed compliance information.

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
