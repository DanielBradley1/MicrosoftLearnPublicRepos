<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getcollectionswithresourcepermissions-method-in-class-sms_rbacsecuredobject -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetCollectionsWithResourcePermissions Method in Class SMS\_RbacSecuredObject

The `GetCollectionsWithResourcePermissions` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the list of collection identifiers for which the user has the specified permissions. The collection must contain the specified resource.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 GetCollectionsWithResourcePermissions(
     UInt32 ResourceID,
     UInt32 Permissions,
     String CollectionIDs[]
);
```

#### Parameters

`ResourceID` Data type: `UInt32`

Qualifiers: \[in\]

Unique ID, supplied by Configuration Manager, for the resource.

`Permissions` Data type: `UInt32`

Qualifiers: \[in\]

Set of user permissions for the collections that contain the resource.

`CollectionIDs` Data type: `String` Array

Qualifiers: \[out\]

IDs of collections for which the user has the specified permissions.

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_RbacSecuredObject Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_rbacsecuredobject-server-wmi-class)
