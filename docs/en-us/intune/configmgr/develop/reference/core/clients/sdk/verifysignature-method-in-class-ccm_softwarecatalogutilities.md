<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/verifysignature-method-in-class-ccm_softwarecatalogutilities -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# VerifySignature Method in Class CCM\_SoftwareCatalogUtilities

The `VerifySignature` Windows Management Instrumentation \(WMI\) class method in Configuration Manager that verifies the data signature.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 VerifySignature
{
    [IN]    String Data
    [IN]    String DataSignature
    [IN]    String WebServiceID
    [IN]    Boolean VerifyUserAndTimestamp
    [OUT]   Boolean SignatureVerificationPassed
};
```

## Parameters

`Data` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Data to verify.

`DataSignature` Data type: `String`

Qualifiers: \[id\("1"\), in\]

Data signature.

`WebServiceID` Data type: `String`

Qualifiers: \[id\("2"\), in\]

Web Service identifier.

`VerifyUserAndTimestamp` Data type: `Boolean`

Qualifiers: \[id\("3"\), in\]

`true` to verify the user and timestamp.

`SignatureVerificationPassed` Data type: `Boolean`

Qualifiers: \[id\("4"\), out\]

`true` if the data signature is valid.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
