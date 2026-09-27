<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ConfigurationItem Server WMI Class

The `SMS_ConfigurationItem` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents a configuration item.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ConfigurationItem : SMS_ConfigurationItemBaseClass
{
      String ApplicabilityCondition;
      String CategoryInstance_UniqueIDs;[]
      UInt32 CI_ID;
      String CI_UniqueID;
      UInt32 CIType_ID;
      UInt32 CIVersion;
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
      Boolean InUse;
      Boolean IsBroken;
      Boolean IsBundle;
      Boolean IsChild;
      Boolean IsDigest;
      Boolean IsEnabled;
      Boolean IsExpired;
      Boolean IsHidden;
      Boolean IsLatest;
      Boolean IsQuarantined;
      Boolean IsSuperseded;
      Boolean IsUserDefined;
      String LastModifiedBy;
      String LocalizedCategoryInstanceNames;[]
      String LocalizedDescription;
      String LocalizedDisplayName;
      SMS_CI_LocalizedEulas LocalizedEulas[];
      SMS_CI_LocalizedProperties LocalizedInformation[];
      String LocalizedInformativeURL;
      UInt32 LocalizedPropertyLocaleID;
      UInt32 ModelID;
      String ModelName;
      UInt32 PermittedUses;
      String PlatformCategoryInstance_UniqueIDs[];
      UInt32 PlatformType;
      SMS_SDMPackageLocalizedData SDMPackageLocalizedData[];
      UInt32 SDMPackageVersion;
      String SDMPackageXML;
      String SecuredScopeNames[];
      String SedoObjectVersion;
      String SourceSite;
};
```

## Methods

The following table lists the methods in the `SMS_ConfigurationItem` class.

| Method | Description |
| --- | --- |
| [AcceptEULA Method in Class SMS\_ConfigurationItem](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/accepteula-method-in-class-sms_configurationitem) | Accepts or declines the Microsoft Software License Terms of a configuration item. |
| [GetEULA Method in Class SMS\_ConfigurationItem](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/geteula-method-in-class-sms_configurationitem) | Gets the localized Microsoft Software License Terms content of the configuration item. |
| [GetSDMDefinition Method in Class SMS\_ConfigurationItem](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/getsdmdefinition-method-in-class-sms_configurationitem) | Retrieves the System Definition Model \(SDM\) definition of the configuration item in XML format. |
| [SetEnforcement Method in Class SMS\_ConfigurationItem](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/setenforcement-method-in-class-sms_configurationitem) | Sets the enforcement and the enforcement date for a configuration item. |

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: \[SizeLimit\("512"\), not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CategoryInstance_UniqueIDs` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[key\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers:\[unique, not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

For this class, the type ID is OtherConfigurationItem \(7\).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

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

`InUse` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

[SMS\_ConfigurationBaselineInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationbaselineinfo-server-wmi-class)

`IsBroken` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

`true` if the configuration item is broken.

`IsBundle` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsChild` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

`true` if this configuration item is a child of other configuration item.

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read, lazy\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsEnabled` Data type: `Boolean`

Access type: `Read/Write`

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

Qualifiers: \[read, not\_null\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read/Write

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

`LocalizedEulas` Data type: `SMS_CI_LocalizedEulas Array`

Access type: Read/Write

Qualifiers: \[lazy\]

An array of localized Microsoft Software License Terms for the configuration item.

`LocalizedDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`LocalizedInformation` Data type: `SMS_CI_LocalizedProperties` Array

Access type: Read/Write

Qualifiers: \[lazy\]

A list of language-specific localized information about the configuration item:

- `String` DisplayName
- `String` Description
- `String` InformativeURL
- `UInt32` LocaleID

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

  Access type: Read-only

  Qualifiers: \[unique, not\_null\]

  See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

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

  `SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData` Array

  Access type: Read/Write

  Qualifiers: \[lazy\]

  See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

  `SDMPackageVersion` Data type: `UInt32`

  Access type: Read-only

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

  Access type: Read-only

  Qualifiers: \[SizeLimit\("3"\)\]

  See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Your application uses this class by creating an object and getting and setting the properties as required for the particular configuration.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes)
