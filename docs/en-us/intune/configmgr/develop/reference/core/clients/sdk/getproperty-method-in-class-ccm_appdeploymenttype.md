<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getproperty-method-in-class-ccm_appdeploymenttype -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetProperty Method in Class CCM\_AppDeploymentType

The `GetProperty` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that retrieves an application deployment type property.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetProperty
{
    [IN]    UInt32 LanguageId
    [IN]    String PropertyName
    [OUT]   String PropertyValue
};
```

## Parameters

`LanguageId` Data type: `UInt32`

Qualifiers: \[id\("0"\), in\]

Language identifier.

`PropertyName` Data type: `String`

Qualifiers: \[id\("1"\), in\]

Property name.

`PropertyValue` Data type: `String`

Qualifiers: \[id\("2"\), out\]

Property value.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
