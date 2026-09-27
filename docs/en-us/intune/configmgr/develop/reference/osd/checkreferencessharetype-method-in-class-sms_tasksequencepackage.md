<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/checkreferencessharetype-method-in-class-sms_tasksequencepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CheckReferencesShareType Method in Class SMS\_TaskSequencePackage

The `CheckReferencesShareType` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, that checks all referred packages for this task sequence and returns all packages that aren't shared.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 CheckReferencesShareType
{
    [IN]    String PackageID
    [OUT]   Boolean CanRunFromDP
    [OUT]   String PacakgeIds[]
    [OUT]   String PackageNames[]
};
```

## Parameters

`PackageID` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Task sequence package identifier.

`CanRunFromDP` Data type: `Boolean`

Qualifiers: \[id\("1"\), out\]

`true` if the package can be run from the distribution point.

`PacakgeIds` Data type: `String Array`

Qualifiers: \[id\("2"\), out\]

Package identifiers for all referred packages for this task sequence that aren't shared.

Note

The incorrect spelling of the variable "PacakgeIds" is hardcoded in WMI.

`PackageNames` Data type: `String Array`

Qualifiers: \[id\("3"\), out\]

Package names for all referred packages for this task sequence that aren't shared.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
