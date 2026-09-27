<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationpolicybase-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ConfigurationPolicyBase Server WMI Class

The `SMS_ConfigurationPolicyBase` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the base class for configuration policy.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationPolicyBase : SMS_ConfigurationItemBaseClass
{
    UInt32 ActivatedCount;
    String ApplicabilityCondition;
    UInt32 AssignedCount;
    String CategoryInstance_UniqueIDs[];
    UInt32 CI_ID;
    String CI_UniqueID;
    UInt32 CIType_ID;
    UInt32 CIVersion;
    UInt32 ComplianceCount;
    Real64 CompliantPercentage;
    UInt64 ConfigurationFlags;
    String CreatedBy;
    DateTime DateCreated;
    DateTime DateLastModified;
    DateTime EffectiveDate;
    UInt32 EULAAccepted;
    Boolean EULAExists;
    DateTime EULASignoffDate;
    String EULASignoffUser;
    UInt32 ExecutionContext;
    UInt32 FailureCount;
    Boolean IsAssigned;
    Boolean IsBroken;
    Boolean IsBundle;
    Boolean IsDigest;
    Boolean IsEnabled;
    Boolean IsExpired;
    Boolean IsHidden;
    Boolean IsLatest;
    Boolean IsQuarantined;
    Boolean IsSuperseded;
    Boolean IsUserDefined;
    String LastModifiedBy;
    String LocalizedCategoryInstanceNames[];
    String LocalizedDescription;
    String LocalizedDisplayName;
    SMS_CI_LocalizedEulas LocalizedEulas[];
    SMS_CI_LocalizedProperties LocalizedInformation[];
    String LocalizedInformativeURL;
    UInt32 LocalizedPropertyLocaleID;
    UInt32 ModelID;
    String ModelName;
    UInt32 NonComplianceCount;
    UInt32 PermittedUses;
    String PlatformCategoryInstance_UniqueIDs[];
    UInt32 PlatformType;
    UInt32 Precedence;
    SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];
    UInt32 SDMPackageVersion;
    String SDMPackageXML;
    String SecuredScopeNames[];
    String SedoObjectVersion;
    UInt32 Severity;
    String SourceSite;
};
```

## Methods

The following table lists the methods in the `SMS_ConfigurationPolicyBase` class.

| Method | Description |
| --- | --- |
| [AcceptEULA Method in Class SMS\_ConfigurationPolicyBase](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/accepteula-method-in-class-sms_configurationpolicybase) | Accepts or declines the Microsoft Software License Terms of a configuration item. |
| [GetEULA Method in Class SMS\_ConfigurationPolicyBase](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/geteula-method-in-class-sms_configurationpolicybase) | Gets the localized Microsoft Software License Terms content, if a configuration item is present. |

## Properties

`ActivatedCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

The number of computers that have evaluated the configuration policy item.

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null, sizelimit\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`AssignedCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

The number of computers or users that have been assigned this configuration policy item.

`CategoryInstance_UniqueIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key, key\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null, unique\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, not\_null, read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ComplianceCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Number of computers that are compliant with the configuration item.

`CompliantPercentage` Data type: `Real64`

Access type: Read-only

Qualifiers: \[not\_null, read\]

The property is deprecated.

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read, sizelimit\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`DateLastModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EffectiveDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EULAAccepted` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EULAExists` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EULASignoffDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EULASignoffUser` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ExecutionContext` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read, valuemap, values\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`FailureCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Represents the number of targets that reported an error during configuration policy evaluation.

`IsAssigned` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[not\_null, read\]

`true` if this is an assigned policy.

`IsBroken` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsBundle` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsExpired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsHidden` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsLatest` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsQuarantined` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read, sizelimit\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String Array`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedDescription` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedEulas` Data type: `SMS_CI_LocalizedEulas Array`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedInformation` Data type: `SMS_CI_LocalizedProperties Array`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedInformativeURL` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`NonComplianceCount` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Number of computers that are not compliant with the configuration item.

`PermittedUses` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`PlatformCategoryInstance_UniqueIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`PlatformType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[bitmap, bitvalues, read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`Precedence` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Precedence represents a resolution order to resolve conflicting rules detected by the rules engine on the client. Currently this is only applicable to EP Firewall configuration policies.

`SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData Array`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SDMPackageVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SDMPackageXML` Data type: `String`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SecuredScopeNames` Data type: `String Array`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`Severity` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

The non-compliance severity of the configuration item.

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: \[sizelimit\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
