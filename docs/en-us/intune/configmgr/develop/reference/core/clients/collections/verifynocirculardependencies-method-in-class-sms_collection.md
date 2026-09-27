<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/verifynocirculardependencies-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# VerifyNoCircularDependencies Method in Class SMS\_Collection

In Configuration Manager, the `VerifyNoCircularDependencies` Windows Management Instrumentation \(WMI\) class method takes two collections as arguments and verifies that no circular dependencies would be formed if one collection were the parent of another.

The following syntax is simplified from Managed Object Format \(MOF\) code and is intended to show the definition of the method.

## Syntax

```
sint32 VerifyNoCircularDependencies(
        SMS_Collection ref parentCollection,
        SMS_Collection ref subCollection,
        boolean Result);
```

#### Parameters

`parentCollection` Data type: `ref:SMS_Collection`

Qualifiers: \[in\]

Reference to an [SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) object path for the parent collection.

`subCollection` Data type: `ref:SMS_Collection`

Qualifiers: \[in\]

Reference to an [SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) object path for the child collection.

`Result` Data type: `Boolean`

Qualifiers: \[out\]

true if there are no circular dependencies, false if there are circular dependencies.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
