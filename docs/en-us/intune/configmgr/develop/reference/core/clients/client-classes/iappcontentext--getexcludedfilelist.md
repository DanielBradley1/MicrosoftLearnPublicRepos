<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iappcontentext--getexcludedfilelist -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# IAppContentExt::GetExcludedFileList

The `IAppContentExt::GetExcludedFileList` method, in Configuration Manager, gets the excluded file list for application content. This is used to support selective file download.

## Syntax

```
[IDL]
HRESULT GetExcludedFileList(
     IWbemClassObject* pHandlerSynclet,
     LPWSTR* pwszExcludedFileList,
     BOOL* pbForceFileExclusion
);
```

#### Parameters

`*pHandlerSynclet` Data type: `IWbemClassObject`

Qualifiers: \[in\]

.

`pwszExcludedFileList` Data type: `LPWSTR`

Qualifiers: \[out\]

The exclude file list is a single string separated by the ':' character. For example, "File1.txt:File2.exe."

`pbForceFileExclusion` Data type: `BOOL`

Qualifiers: \[out\]

`True` to force exclusion of files. If `False`, content framework decides whether or not excluding them based on network condition and content configuration.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following one:

S\_OK Discovery was triggered successfully. All other return values indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Microsoft.ConfigurationManagement.ApplicationManagement](https://learn.microsoft.com/en-us/previous-versions/)\] [Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference)
