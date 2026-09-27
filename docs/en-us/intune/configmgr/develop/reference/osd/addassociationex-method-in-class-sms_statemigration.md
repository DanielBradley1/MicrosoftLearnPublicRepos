<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/addassociationex-method-in-class-sms_statemigration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# AddAssociationEx Method in Class SMS\_StateMigration

The `AddAssociationEx` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, adds the computer association between two system resources used in state migration.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 AddAssociationEx(
      UInt32 SourceClientResourceID,
      UInt32 RestoreClientResourceID,
      UInt32 MigrationBehavior,
      SMS_StateMigrationUserNames UserNames[]
);
```

#### Parameters

`SourceClientResourceID` Data type: `UInt32`

Qualifiers: \[in\]

Resource ID for the source client.

`RestoreClientResourceID` Data type: `UInt32`

Qualifiers: \[in\]

Resource ID for the destination client.

`MigrationBehavior` Data type: `UInt32`

Qualifiers: \[in\]

Migration behavior. Possible values are:

| Value | Migration behavior |
| --- | --- |
| 0 | CAPTUREANDRESTOREALL |
| 1 | CAPTUREALLRESTORESPECIFIED |
| 2 | CAPTUREANDRESTORESPECIFIED |

`UserNames` Data type: `SMS_StateMigrationUserNames` Array

Qualifiers: \[in\]

[SMS\_StateMigrationUserNames Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigrationusernames-server-wmi-class) objects representing the names of users with profiles to be migrated. These objects are defined by the `UserNames` property of [SMS\_StateMigration Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigration-server-wmi-class).

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

For an example of the use of this method, see [How to Create an Association Between Two Computers in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-association-between-two-computers-in-configuration-manager). To remove an association, your application can call the [DeleteAssociation Method in Class SMS\_StateMigration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/deleteassociation-method-in-class-sms_statemigration).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_StateMigration Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigration-server-wmi-class) [SMS\_StateMigrationUserNames Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigrationusernames-server-wmi-class) [DeleteAssociation Method in Class SMS\_StateMigration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/deleteassociation-method-in-class-sms_statemigration) [How to Create an Association Between Two Computers in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-association-between-two-computers-in-configuration-manager)
