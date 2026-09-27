<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_deploymenttype-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DeploymentType Server WMI Class

The `SMS_DeploymentType` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the deployment type of an application. This is read-only class. For creation, modification, or deletion of deployment types, refer to [SMS\_Application Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_application-server-wmi-class).

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DeploymentType : SMS_ConfigurationItemBaseClass
{
    String ApplicabilityCondition;
    String AppModelName;
    String CategoryInstance_UniqueIDs[];
    UInt32 CI_ID;
    String CI_UniqueID;
    UInt32 CIType_ID;
    UInt32 CIVersion;
    UInt64 ConfigurationFlags;
    String ContentId;
    String CreatedBy;
    DateTime DateCreated;
    DateTime DateLastModified;
    Boolean Dependencies;
    DateTime EffectiveDate;
    UInt32 EnforcementSuccess;
    UInt32 EULAAccepted;
    Boolean EULAExists;
    DateTime EULASignoffDate;
    String EULASignoffUser;
    UInt32 ExecutionContext;
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
    String ModelName;
    UInt32 ModelID;
    UInt32 NumberOfDependedDTs;
    UInt32 NumberOfDependentDTs;
    UInt32 PermittedUses;
    String PlatformCategoryInstance_UniqueIDs[];
    UInt32 PlatformType;
    UInt32 PriorityInLatestApp;
    SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];
    UInt32 SDMPackageVersion;
    String SDMPackageXML;
    String SecuredScopeNames[];
    String SedoObjectVersion;
    String SourceSite;
    String Technology;
};
```

## Methods

The following table lists the methods in the `SMS_DeploymentType` class.

| Method | Description |
| --- | --- |
| [DistributeDeploymentTypeExtension Method in Class SMS\_DeploymentType](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/distributedeploymenttypeextension-method-in-class-sms_deploymenttype) | Schedules a Deployment Type Extension to be distributed throughout the hierarchy. |

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null, sizelimit\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`AppModelName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Name of the model for the application model name.

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

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ContentId` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Content ID.

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

`Dependencies` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

`True` if this deployment has dependencies, otherwise `False`.

`EffectiveDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`EnforcementSuccess` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Number of successful client installations or clients that have the deployment already installed.

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

`LocalizedInformativeURL` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ModelID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`NumberOfDependedDTs` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Number of deployment types that this deployment type is dependent on.

`NumberOfDependents` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Number of deployment types that depend on this deployment type.

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

`PriorityInLatestApp` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Priority of the deployment type in the latest application revision.

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

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: \[sizelimit\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`Technology` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Technology description.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
