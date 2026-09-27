<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getsiteadinfo-method-in-class-sms_site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetSiteADInfo Method in Class SMS\_Site

The `GetSiteADInfo` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets Active Directory information of site server.

The following syntax is simplified from Managed Object Format \(MOF\) code and is intended to show the definition of the method.

## Syntax

```
SInt32 GetSiteADInfo(
   String SiteCode,
   String DCName,
   String DCAddress,
   String DomainName,
   String ForestName,
   String DCSiteName,
   String ClientSiteName
);
```

#### Parameters

`SiteCode` Data type: `String`

Qualifiers: \[in\]

Site code.

`DCName` Data type: `String`

Qualifiers: \[out\]

Name of the Active Directory domain controller.

`DCAddress` Data type: `String`

Qualifiers: \[out\]

Domain controller address.

`DomainName` Data type: `String`

Qualifiers: \[out\]

Domain name.

`ForestName` Data type: `String`

Qualifiers: \[out\]

Name of the Active Directory forest.

`DCSiteName` Data type: `String`

Qualifiers: \[out\]

Name of the Active Directory site where the domain controller is located.

`ClientSiteName` Data type: `String`

Qualifiers: \[out\]

Name of the site that the computer belongs to.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Identification Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class)
