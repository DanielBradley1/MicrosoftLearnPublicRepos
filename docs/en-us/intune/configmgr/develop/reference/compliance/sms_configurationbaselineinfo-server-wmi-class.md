<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationbaselineinfo-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ConfigurationBaselineInfo Server WMI Class

The `SMS_ConfigurationBaselineInfo` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a baseline configuration item. For more information about this type of configuration item, see [SMS\_BaselineAssignment Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class).

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationBaselineInfo : SMS_ConfigurationItemBaseClass
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
      Boolean InUse;
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
      String LocalizedInformativeURL;
      UInt32 LocalizedPropertyLocaleID;
      UInt32 ModelID;
      String ModelName;
      UInt32 NonComplianceCount;
      UInt32 PermittedUses;
      String PlatformCategoryInstance_UniqueIDs[];
      UInt32 PlatformType;
      SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];
      UInt32 SDMPackageVersion;
      String SDMPackageXML;
      String SecuredScopeNames[];
      String SedoObjectVersion;
      UInt32 Severity;
      String SourceSite;
      Real64 TargetCompliance;
};
```

## Methods

The `SMS_ConfigurationBaselineInfo` class does not define any methods.

## Properties

`ActivatedCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

The number of computers that have evaluated the configuration item.

`ApplicabilityCondition` Data type: `String`

Access type: Read

Qualifiers: \[SizeLimit\("512"\), not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`AssignedCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

The number of computers that are targeted with the configuration item.

`CategoryInstance_UniqueIDs` Data type: `String` Array

Access type: Read

Qualifiers: None

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read

Qualifiers: \[key\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read

Qualifiers:\[unique, not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class)..

For this class, the type ID is Baseline \(2\).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ComplianceCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

Number of computers that are compliant with the configuration item.

`CompliantPercentage` Data type: `Real64`

Access type: Read/Write

Qualifiers: none

The property is deprecated. Use the information contained in the [SMS\_DeploymentSummary Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_deploymentsummary-server-wmi-class) instead.

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: \[SizeLimit\("512"\), read, not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read, not\_null\]

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

Access type: Read

Qualifiers: None

Number of computers that failed to evaluate the configuration item.

`InUse` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if the configuration item is in use. A configuration item is used, if it is referenced by other baseline or its setting is referenced by other configuration item.

`IsAssigned` Data type: `Boolean`

Access type: Read

Qualifiers: None

`true` if the configuration item is assigned. The default value is `false`.

`IsBundle` Data type: `Boolean`

Access type: Read

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsBroken` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

`true` if the configuration item is broken, otherwise, the value is `false`.

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read, lazy\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsEnabled` Data type: `Boolean`

Access type: Read

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsExpired` Data type: `Boolean`

Access type: Read

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsHidden` Data type: `Boolean`

Access type: Read

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

This property is not used for desired configuration management.

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: \[SizeLimit\("512"\), read, not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String` Array

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

Access type: Read

Qualifiers: \[unique, not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`NonComplianceCount` Data type: `UInt32`

Access type: Read

Qualifiers: None

Number of computers that are not compliant with the configuration item.

`PermittedUses` Data type: `UInt32`

Access type: Read

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

`SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData` Array

Access type: Read

Qualifiers: \[lazy\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SDMPackageVersion` Data type: `UInt32`

Access type: Read

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`SDMPackageXML` Data type: `String`

Access type: Read

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

Access type: Read

Qualifiers: None

The noncompliance severity of the configuration item.

`SourceSite` Data type: `String`

Access type: Read

Qualifiers: \[SizeLimit\("3"\)\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`TargetCompliance` Data type: `Real64`

Access type: Read/Write

Qualifiers: none

The property is deprecated. Use the information contained in the [SMS\_DeploymentSummary Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_deploymentsummary-server-wmi-class) class instead.

## Remarks

Class qualifiers for this class include:

- Secured
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Your application can use this class to create a baseline. After creating the object, the application should set the `CIType_ID` property to Baseline \(2\). When the object is properly configured, the application can use the [SMS\_BaselineAssignment Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class) class to populate it with other configuration items and corresponding rules.

  For information on the use of this class, see How to List Configuration Assignments and How to Assign Configuration Baselines. An example for baseline configuration is provided in Configuration Baseline Example 1.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes) [SMS\_BaselineAssignment Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class)
