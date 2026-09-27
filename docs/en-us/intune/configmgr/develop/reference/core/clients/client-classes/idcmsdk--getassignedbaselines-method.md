<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk--getassignedbaselines-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# IDCMSDK::GetAssignedBaselines Method

The `IDCMSDK::GetAssignedBaselines` method, in Configuration Manager, enumerates assigned baseline configuration items.

## Syntax

```
[IDL]
HRESULT GetAssignedBaselines(
     IEnumUnknown**  ppEnum,
     ULONG*  pulNumCIs,
     struct CIDetectInfo**  ppInfo
);
```

#### Parameters

`ppEnum` Data type: `IEnumUnknown`

Qualifiers: \[out\]

Pointer to a pointer to an enumeration object containing an [ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface) for each baseline configuration item currently assigned and downloaded to the client.

`pulNumCIs` Data type: `ULONG`

Qualifiers: \[out\]

Pointer to the number of baseline configuration items. On successful return from the method, this parameter also indicates the number of other configuration items currently assigned to the client.

`ppInfo` Data type: `struct`

Qualifiers: \[out, size\_is\(,\*pulNumCIs\)\]

Pointer to a pointer to a [CIDetectInfo Structure](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cidetectinfo-structure) containing information for each baseline configuration item that is assigned but not downloaded.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following:

S\_OK The method succeeded. All other values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[IDCMSDK Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/idcmsdk-interface) [ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface) [CIDetectInfo Structure](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cidetectinfo-structure)
