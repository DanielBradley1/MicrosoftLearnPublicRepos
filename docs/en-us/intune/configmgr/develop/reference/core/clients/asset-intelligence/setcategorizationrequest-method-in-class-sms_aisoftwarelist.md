<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/setcategorizationrequest-method-in-class-sms_aisoftwarelist -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetCategorizationRequest Method in Class SMS\_AISoftwareList

The `SetCategorizationRequest` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, initiates a System Center Online software categorization request.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 SetCategorizationRequest(
     String SoftwareKey,
);
```

#### Parameters

`SoftwareKey` Data type: `String`

Qualifiers: \[in\]

Hash of the software to be categorized. After this method is called, the hash is sent to the System Center Online server to be categorized during its next release.

This property name has changed from `SoftwarePropertiesHash` to `SoftwareKey` in SP1.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_AISoftwareList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aisoftwarelist-server-wmi-class)
