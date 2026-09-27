<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/applypolicyex-method-in-class-ccm_softwarecatalogutilities -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# ApplyPolicyEx Method in Class CCM\_SoftwareCatalogUtilities

The `ApplyPolicyEx` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that applies policy.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 ApplyPolicyEx
{
    [IN]    String Body
    [IN]    String BodySignature
    [IN]    String BodySource
    [OUT]   String Id
};
```

## Parameters

`Body` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Policy body.

`BodySignature` Data type: `String`

Qualifiers: \[id\("1"\), in\]

Policy body signature.

`BodySource` Data type: `String`

Qualifiers: \[id\("2"\), in\]

Policy body source.

`Id` Data type: `String`

Qualifiers: \[id\("3"\), out\]

Identifier.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
