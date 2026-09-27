<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/gettspolicies-method-in-class-sms_tasksequencepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetTsPolicies Method in Class SMS\_TaskSequencePackage

The `GetTsPolicies` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets all policies associated with the specified task sequence. The user must have rights to create media other than stand-alone.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetTsPolicies(
     String AdvertisementID,
     String PackageID,
     SMS_TaskSequence TaskSequence,
     String AdvertisementName,
     String AdvertisementComment,
     UInt32 AdvertisementFlags,
     String BootImageID,
     String SourceSite,
     String PolicyXmls[],
     String PolicyAssignmentXmls[]
);
```

#### Parameters

`AdvertisementID` Data type: `String`

Qualifiers: \[in\]

A user-defined advertisement ID to embed in the policy. This ID should not conflict with other advertisement IDs that have been created by the site.

`PackageID` Data type: `String`

Qualifiers: \[in\]

The ID for the task sequence package, if the method is to obtain policy for a task sequence stored in the Configuration Manager database. Either `PackageID` or `TaskSequence` can be non-null, but not both parameters.

`TaskSequence` Data type: `SMS_TaskSequence`

Qualifiers: \[in\]

[SMS\_TaskSequence Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) object representing the task sequence. Either `PackageID` or `TaskSequence` can be non-null, but not both parameters.

`AdvertisementName` Data type: `String`

Qualifiers: \[in\]

A user-defined name for the advertisement.

`AdvertisementComment` Data type: `String`

Qualifiers: \[in\]

A user-defined comment for the advertisement.

`AdvertisementFlags` Data type: `UInt32`

Qualifiers: \[in\]

User-defined flags specifying advertisement details. See [SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class) for more information about these flags.

`BootImageID` Data type: `String`

Qualifiers: \[in\]

The ID for a boot image package to use with the task sequence. This parameter is required if the `TaskSequence` parameter is defined. Otherwise, it must be set to `null`.

`SourceSite` Data type: `String`

Qualifiers: \[in\]

Code for the source site for the advertisement.

`PolicyXmls` Data type: `String` Array

Qualifiers: \[out\]

XML strings representing the policy for the specified task sequence and dependent policies.

`PolicyAssignmentXmls` Data type: `String` Array

Qualifiers: \[out\]

XML strings representing assignments for the policy specified by `PolicyXmls`. `PolicyXmls` and `PolicyAssignmentXmls` are aligned, with the nth element of one parameter corresponding to the nth element of the other.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

The policies for a task sequence include the policy for the task sequence itself, policies for all referenced packages, and corresponding policy assignments. The task sequence can be stored either in the database or in memory as a set of WMI objects.

If the task sequence is in the Configuration Manager database, your application should specify the package identifier for the task sequence package in the `PackageID` parameter. If supplying a value for this parameter, you must have read permission for the specific task sequence.

If the task sequence is in memory, your application must specify values for the `TaskSequence` and `BootImageID` parameters.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Advertisement Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_advertisement-server-wmi-class) [SMS\_TaskSequencePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) [GetClientConfigPolicies Method in Class SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getclientconfigpolicies-method-in-class-sms_tasksequencepackage) [GetSequence Method in Class SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage) [SetSequence Method in Class SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage)
