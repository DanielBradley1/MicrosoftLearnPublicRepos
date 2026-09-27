<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/getcategorizationrequesttext-method-in-class-sms_aisoftwarelist -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetCategorizationRequestText Method in Class SMS\_AISoftwareList

The `GetCategorizationRequestText` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, retrieves the XML that is sent to System Center Online for categorization.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetCategorizationRequestText(
     String SoftwareKey,
     String CategorizationRequestText
);
```

#### Parameters

`SoftwareKey` Data type: `String`

Qualifiers: \[in\]

The MD5 hash of the software to be categorized. The hash is made up of the software name, publisher, and version.

This property name has changed from `SoftwarePropertiesHash` to `SoftwareKey` in SP1.

`CategorizationRequestText` Data type: `String`

Qualifiers: \[out\]

XML formatted string which contains the hash, name, version, publisher, evidence type, and system default locale identifier \(LCID\) of the software.

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
