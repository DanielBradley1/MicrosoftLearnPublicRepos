<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/gettsrelatedtodrivercategory-method-in-class-sms_tasksequencepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetTSRelatedToDriverCategory Method in Class SMS\_TaskSequencePackage

The `GetTSRelatedToDriverCategory` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, that gets task sequence packages related to the specified category.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 GetTSRelatedToDriverCategory
{
    [IN]    String CategoryUniqueId,
    [OUT]   String PacakgeIds[]
    [OUT]   String PackageNames[]
};
```

## Parameters

`CategoryUniqueId` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Unique ID of the category instance. This ID is unique across sites. The string length can be up to 512 characters.

`PacakgeIds` Data type: `String` Array

Qualifiers: \[id\("2"\), out\]

Package identifiers for packages related to the specified category.

Note

The incorrect spelling of the variable "PacakgeIds" is hardcoded in WMI.

`PackageNames` Data type: `String` Array

Qualifiers: \[id\("3"\), out\]

Package names for packages related to the specified category.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
