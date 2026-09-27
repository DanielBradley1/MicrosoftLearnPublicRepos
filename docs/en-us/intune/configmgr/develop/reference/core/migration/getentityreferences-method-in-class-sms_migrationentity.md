<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/getentityreferences-method-in-class-sms_migrationentity -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetEntityReferences Method in Class SMS\_MigrationEntity

The `GetEntityReferences` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the referenced entities of the specified entities.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetEntityReferences(
     UInt32 entityIDs[],
     UInt32 referenceType,
     Boolean referenceDirection,
     UInt32 entityReferenceList[]
);
```

#### Parameters

`entityIDs` Data type: `UInt32` array

Qualifiers: \[in\]

List of entities input.

`referenceType` Data type: `UInt32`

Qualifiers: \[in\]

Reference type.

`referenceDirection` Data type: `Boolean` array

Qualifiers: \[in\]

A flag indicating whether this is querying referencing or being referenced.

`entityReferenceList` Data type: `UInt32` Array

Qualifiers: `[out]`

List of entities queried.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_MigrationEntity Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/migration/sms_migrationentity-server-wmi-class)
