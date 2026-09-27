<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getnextservicewindowid-method-in-class-ccm_servicewindowmanager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetNextServiceWindowID Method in Class CCM\_ServiceWindowManager

The `GetNextServiceWindowID` WMI class method, in Configuration Manager, gets the identifier of the next service window instance closest to the current time.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetNextServiceWindowID(
     [OUT] String NextServiceWindowID
);
```

#### Parameters

`NextServiceWindowID` Data type: `String`

Qualifiers: \[out\]

Identifier of the next service window instance closest to the current time.

## Return Values

A `UInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[CCM\_ServicewindowManager Client WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_servicewindowmanager-client-wmi-class)
