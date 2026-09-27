<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getjobstate-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICIINFO::GetJobState Method

The `ICIINFO::GetJobState` method, in Configuration Manager, gets the current operational state of the configuration item that is part of a job or task.

## Syntax

```
[IDL]
HRESULT GetJobState(
    CIJobState* pCIJobState,
     Percentage* ppctComplete,
     HRESULT* phrStatus
);
```

#### Parameters

`pCIJobState` Data type: `CIJobState`

Qualifiers: \[out\]

Pointer to a [CIJobState Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cijobstate-enumeration) value indicating the current operational state of the configuration item. This parameter retrieves ciStatusError if the state is not available.

`ppctComplete` Data type: `Percentage`

Qualifiers: \[out\]

Pointer to a `Percentage` object indicating the percentage of job completion.

`phrStatus` Data type: `HRESULT`

Qualifiers: \[out\]

Pointer to an `HRESULT` code representing the current status. This parameter indicates an error code if `pCIJobState` retrieves a value of ciStatusError.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface) [CIJobState Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cijobstate-enumeration)
