<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/itsenvclass--getvariables-method -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ITSEnvClass::GetVariables Method

In Configuration Manager, the `GetVariables` method gets the variables for the operating system deployment task sequence environment.

## Syntax

```
[IDL]
HRESULT GetVariables(
     VARIANT* variables
);
```

#### Parameters

`variables` Data type: `VARIANT`

Qualifiers: \[out, retval\]

Pointer to the environment variables.

## Return Values

An `HRESULT` code. Possible values include, but are not limited to, the following value.

S\_OK The method succeeded.

## See Also

[ITSEnvClass Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/itsenvclass-interface)
