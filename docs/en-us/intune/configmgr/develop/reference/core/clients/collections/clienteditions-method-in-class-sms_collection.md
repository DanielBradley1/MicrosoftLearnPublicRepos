<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/clienteditions-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ClientEditions Method in Class SMS\_Collection

The `ClientEditions` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, retrieves a list of client editions and whether the `DeviceOwner` property may be edited.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ClientEditions(
     UInt32 ClientEdition[],
     Boolean Editable[]
);
```

#### Parameters

`ClientEdition` Data type: `UInt32` Array

Qualifiers: \[out\]

Edition of the client. Possible values are:

| Value | Client edition |
| --- | --- |
| 0 | Desktop |
| 1 | Windows RT |
| 2 | Windows Mobile 6 |
| 3 | Nokia Symbian |
| 4 | Windows Phone |
| 5 | Mac |
| 6 | Windows CE |
| 7 | Windows Embedded |
| 8 | iOS |
| 9 | iPad |
| 10 | iPodTouch |
| 11 | Andriod |
| 12 | iSocConsumer |
| 13 | Unix/Linux |

`Editable` Data type: `Boolean` Array

Qualifiers: \[out\]

`true` if the `DeviceOwner` property may be edited.

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
