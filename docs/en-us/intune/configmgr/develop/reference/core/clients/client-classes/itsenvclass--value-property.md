<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/itsenvclass--value-property -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# ITSEnvClass::Value Property

In Configuration Manager, the `Value` property contains the value of an operating system deployment task sequence environment variable.

## Syntax

```
[IDL]
HRESULT Value([in] BSTR Name, [in] BSTR Value);

HRESULT Value([in] BSTR Name, [out,retval] BSTR* Value);
```

#### Parameters

`Name` Data type: `BSTR`

Qualifiers: \[in\]

The name of the environment variable.

`Value` Data type: `BSTR`

Qualifiers: \[in; out, retval\]

On input, the value to set for the environment variable. On output, this parameter points to the value that is retrieved for the supplied name.

## Return Values

An `HRESULT` code. Possible values include, but aren't limited to, the following value.

S\_OK The method succeeded.

## Remarks

The `get_Value` function succeeds with S\_OK when called with an invalid variable name, but retrieves an empty string for the value. This behavior differs from the more common return of a non-zero exit code to indicate an invalid variable name input.

## See Also

[ITSEnvClass Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/itsenvclass-interface)
