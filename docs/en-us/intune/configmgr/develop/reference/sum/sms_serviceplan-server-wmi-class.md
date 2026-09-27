<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_serviceplan-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# SMS\_ServicePlan Server WMI Class

The `SMS_ServicePlan` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a service plan.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ServicePlan : SMS_SoftwareUpdateBase  
{  
    String ApplicabilityCondition;  
    String ArticleID;  
    String BulletinID;  
    String CategoryInstance_UniqueIDs[];  
    UInt32 CI_ID;  
    String CI_UniqueID;  
    UInt32 CIType_ID;  
    UInt32 CIVersion;  
    UInt64 ConfigurationFlags;  
    String CreatedBy;  
    UInt32 CustomSeverity;  
    String CustomSeverityName;  
    DateTime DateCreated;  
    DateTime DateLastModified;  
    DateTime DatePosted;  
    DateTime DateRevised;  
    DateTime EffectiveDate;  
    UInt32 EULAAccepted;  
    Boolean EULAExists;  
    DateTime EULASignoffDate;  
    String EULASignoffUser;  
    UInt32 ExecutionContext;  
    Boolean IsBundle;  
    Boolean IsContentProvisioned;  
    Boolean IsDeployable;  
    Boolean IsDeployed;  
    Boolean IsDigest;  
    Boolean IsEnabled;  
    Boolean IsExpired;  
    Boolean IsHidden;   
    Boolean IsLatest;  
    Boolean IsMetadataOnlyUpdate;  
    Boolean IsOfflineServiceable;  
    Boolean IsQuarantined;  
    Boolean IsSuperseded;  
    Boolean IsUserDefined;  
    String LastModifiedBy;  
    DateTime LastStatusTime;  
    String LocalizedCategoryInstanceNames[];  
    String LocalizedDescription;  
    String LocalizedDisplayName;  
    SMS_CI_LocalizedEulas LocalizedEulas[];  
    SMS_CI_LocalizedProperties LocalizedInformation[];  
    String LocalizedInformativeURL;  
    UInt32 LocalizedPropertyLocaleID;   
    UInt32 MaxExecutionTime;  
    UInt32 ModelID;  
    String ModelName;   
    UInt32 NumMissing;  
    UInt32 NumNotApplicable;  
    UInt32 NumPresent;  
    UInt32 NumTotal;  
    UInt32 NumUnknown;  
    UInt32 PercentCompliant;  
    UInt32 PermittedUses;   
    String PlatformCategoryInstance_UniqueIDs[];  
    UInt32 PlatformType;  
    Boolean RequiresExclusiveHandling;  
    UInt32 RevisionNumber;  
    SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];  
    UInt32 SDMPackageVersion;  
    String SDMPackageXML;   
    String SecuredScopeNames[];  
    String SedoObjectVersion;  
    UInt32 Severity;  
    String SeverityName;  
    SInt64 Size;  
    String SourceSite;  
    String UpdateLocales[];  
};  
```

## Methods

The `SMS_ServicePlan` class does not define any methods.

## Properties

`ApplicabilityCondition`  
Data type: `String`

Access type: Read/Write

Qualifiers: \[SizeLimit\("512"\), not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`ArticleID`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read, SizeLimit\("64"\), not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`BulletinID`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read, SizeLimit\("64"\), not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`CategoryInstance_UniqueIDs`  
Data type: `String` Array

Access type: Read/Write

Qualifiers: None

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`CI_ID`  
Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`CI_UniqueID`  
Data type: `String`

Access type: Read/Write

Qualifiers: \[unique, not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`CIType_ID`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read, enumeration\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`CIVersion`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`ConfigurationFlags`  
Data type: `UInt64`

Access type: Read-only

Qualifiers: \[bits\("COMPLIANCE\_POLICY\(0\)"\), read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`CreatedBy`  
Data type: `String`

Access type: Read-only

Qualifiers: \[SizeLimit\("512"\),read, not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`CustomSeverity`  
Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`CustomSeverityName`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`DateCreated`  
Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`DateLastModified`  
Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`DatePosted`  
Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`DateRevised`  
Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`EffectiveDate`  
Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`EULAAccepted`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`EULAExists`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`EULASignoffDate`  
Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`EULASignoffUser`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`ExecutionContext`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read, valuemap, values\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsBundle`  
Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsContentProvisioned`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsDeployable`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsDeployed`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsDigest`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsEnabled`  
Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsExpired`  
Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsHidden`  
Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsLatest`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsMetadataOnlyUpdate`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsOfflineServiceable`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsQuarantined`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsSuperseded`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`IsUserDefined`  
Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`LastModifiedBy`  
Data type: `String`

Access type: Read-only

Qualifiers: \[SizeLimit\("512"\), read, not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`LastStatusTime`  
Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`LocalizedCategoryInstanceNames`  
Data type: `String Array`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`LocalizedDescription`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`LocalizedDisplayName`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`LocalizedEulas[]`  
Data type: `SMS_CI_LocalizedEulas`

Access type: \[read,lazy\]

Qualifiers: none

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`LocalizedInformation[]`  
Data type: `SMS_CI_LocalizedProperties`

Access type: \[read, lazy\]

Qualifiers: none

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`LocalizedInformativeURL`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`LocalizedPropertyLocaleID`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`MaxExecutionTime`  
Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`ModelID`  
Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`ModelName`  
Data type: `String`

Access type: Read/Write

Qualifiers: \[unique, not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`NumMissing`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`NumNotApplicable`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`NumPresent`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`NumTotal`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`NumUnknown`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`PercentCompliant`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`PermittedUses`  
Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`PlatformCategoryInstance_UniqueIDs`  
Data type: `String Array`

Access type: Read/Write

Qualifiers: none

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`PlatformType`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[bitmap, bitvalues, read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`RequiresExclusiveHandling`  
Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`RevisionNumber`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`SDMPackageLocalizedData`  
Data type: `SMS_SDMPackageLocalizedData` Array

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`SDMPackageVersion`  
Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`SDMPackageXML`  
Data type: `String`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`SecuredScopeNames`  
Data type: `String Array`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`SedoObjectVersion`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`Severity`  
Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`SeverityName`  
Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`Size`  
Data type: `sint64`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`SourceSite`  
Data type: `String`

Access type: Read/Write

Qualifiers: \[SizeLimit\("3"\)\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

`UpdateLocales`  
Data type: `String Array`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SoftwareUpdateBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatebase-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
