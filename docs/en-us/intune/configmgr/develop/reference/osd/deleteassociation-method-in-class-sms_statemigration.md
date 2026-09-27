<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/deleteassociation-method-in-class-sms_statemigration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# DeleteAssociation Method in Class SMS\_StateMigration

The `DeleteAssociation` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, deletes the computer association between two system resources used in state migration.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 DeleteAssociation(
      UInt32 SourceClientResourceID,
      UInt32 RestoreClientResourceID
);
```

#### Parameters

`SourceClientResourceID` Data type: `UInt32`

Qualifiers: \[in\]

Resource ID for the source client.

`RestoreClientResourceID` Data type: `uint32`

Qualifiers: \[in\]

Resource ID for the destination client.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

Your application uses this method to remove an association that has been created by using a call to the [AddAssociation Method in Class SMS\_StateMigration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/addassociation-method-in-class-sms_statemigration).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_StateMigration Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigration-server-wmi-class) [AddAssociation Method in Class SMS\_StateMigration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/addassociation-method-in-class-sms_statemigration)
