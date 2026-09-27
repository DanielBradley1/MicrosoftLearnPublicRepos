<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/getdependency-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetDependency method in class SMS\_Collection

Starting in version 2010, the `GetDependency` WMI class method in Configuration Manager gets the collection relationship info which the input collection depends on.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```MOF
sint32 GetDependency(
    string Relationship[]
);
```

## Parameters

### `Relationship`

Data type: `String[]` \(array\)

Qualifiers: \[out\]

JSON string array of collection dependency relationship.

## Return values

An `SInt32` data type that is `0` to indicate success, or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_Collection server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class)

[GetDependent method](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/getdependent-method-in-class-sms_collection)
