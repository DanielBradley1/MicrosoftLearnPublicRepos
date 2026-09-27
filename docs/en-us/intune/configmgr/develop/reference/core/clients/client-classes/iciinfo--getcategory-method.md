<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo--getcategory-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ICIINFO::GetCategory Method

The `ICIINFO::GetCategory` method, in Configuration Manager, gets a localized category name by index and the group name of the category.

## Syntax

```
[IDL]
HRESULT GetCategory(
     ULONG ulIndex,
     LanguageId* pLanguageId,
     LPWSTR* ppszCategoryGroup,
     LPWSTR* ppszCategoryName
);
```

#### Parameters

`ulIndex` Data type: `ULONG`

Qualifiers: \[in\]

Index of the category to retrieve.

`pLanguageId` Data type: `LanguageId`

Qualifiers: \[in, out\]

Pointer to a language ID used to obtain the localized category name. If there is no localized name for this ID, the method attempts to obtain the language-independent string. If this does not exist, the method returns an error. On successful return from the method, this parameter indicates the language ID for the localized category name.

`ppszCategoryGroup` Data type: `LPWSTR`

Qualifiers: \[out\]

Pointer to the category group.

`ppszCategoryName` Data type: `LPWSTR`

Qualifiers: \[out\]

Pointer to the localized name of the category.

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
