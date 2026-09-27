<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/gettotalnumresults-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetTotalNumResults Method in Class SMS\_Collection

The `GetTotalNumResults` Windows Management Instrumentation \(WMI\) class method gets a count of all members in a collection, including subcollections.

The following syntax is simplified from Managed Object Format \(MOF\) code and is intended to show the definition of the method.

## Syntax

```
SInt32 GetTotalNumResults(
     ref:SMS_Collection Collection,
     UInt32 Result
);
```

#### Parameters

`Collection` Data type: `ref:SMS_Collection`

Qualifiers: \[in\]

Collection ID or object path of the collection. The collection ID is the value of the `CollectionID` property of [SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class).

`Result` Data type: `UInt32`

Qualifiers: \[out\]

Number of collection members, including subcollections.

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
