<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/getclientscountbycollections-method-in-class-sms_migrationcollectioninfo -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetClientsCountByCollections Method in Class SMS\_MigrationCollectionInfo

The `GetClientsCountByCollections` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, retrieves the number of clients in the specified collections.

Note

This method is reserved for future use.

The following syntax is simplified from Managed Object Format \(MOF\) code and is intended to show the definition of the method.

## Syntax

```
SInt32 GetClientsCountByCollections(
     String collectionIDs[],
     UInt32 clientsCount
);
```

#### Parameters

`collectionIDs` Data type: `String` array

Qualifiers: \[in\]

The specified collection IDs.

`clientsCount` Data type: `UInt32`

Qualifiers: `[out]`

The number of clients in the collections.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_MigrationCollectionInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationcollectioninfo-server-wmi-class)
