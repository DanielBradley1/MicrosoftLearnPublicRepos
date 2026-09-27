<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getbaselinecompliancereport-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IDCMSDK::GetBaselineComplianceReport Method

The `IDCMSDK::GetBaselineComplianceReport` method, in Configuration Manager, retrieves the cached discovery report for the specified configuration item baseline.

## Syntax

```
[IDL]
HRESULT GetBaselineComplianceReport(
     LPCWSTR  pszId,
     LPCWSTR  pszVersion,
     LPWSTR*  ppszComplianceInfo
);
```

#### Parameters

`pszId` Data type: `LPCWSTR`

Qualifiers: \[in\]

Pointer to a null-terminated string specifying the ID of the baseline configuration item. An example ID is "ScopeId\_6CD81FFE-63C4-4AF6-B50A-0847707628A0/Baseline\_780a1633-ba4d-4172-b2b1-583cc733ef56".

`pszVersion` Data type: `LPCWSTR`

Qualifiers: \[in, unique\]

Pointer to a null-terminated string specifying the baseline configuration item version. If this parameter is set to `null`, the method retrieves the latest version of the baseline configuration item that exists in the client data store.

`ppszComplianceInfo` Data type: `LPWSTR`

Qualifiers: \[out\]

Pointer to a null-terminated string specifying a report of compliance information for the baseline configuration item.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[IDCMSDK Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk-interface)
