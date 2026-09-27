<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_passportforworkprofilesettings-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_PassportForWorkProfileSettings Server WMI Class

The `SMS_PassportForWorkProfileSettings` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents Windows Hello for Business profile settings.

Note

Windows Hello for Business was previously known as Microsoft Passport for Work.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_PassportForWorkProfileSettings : SMS_SettingsDefinitionBase
{
    String ApplicabilityCondition;
    String CategoryInstance_UniqueIDs[];
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

The `SMS_PassportForWorkProfileSettings` class does not define any methods.

## Properties

`ApplicabilityCondition` Data type: `String`

Access type: Read/Write

Qualifiers: \[SizeLimit\("512"\), not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`CategoryInstance_UniqueIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: None

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`CI_UniqueID` Data type: `String`

Access type: Read/Write

Qualifiers:\[unique, not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`CIType_ID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`CIVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`ConfigurationFlags` Data type: `UInt64`

Access type: Read-only

Qualifiers: \[bits\("COMPLIANCE\_POLICY\(0\)"\), read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`CreatedBy` Data type: `String`

Access type: Read-only

Qualifiers: \[SizeLimit\("512"\),read, not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`DateCreated` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`DateLastModified` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`EffectiveDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`EULAAccepted` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`EULAExists` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`EULASignoffDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`EULASignoffUser` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`ExecutionContext` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read, valuemap, values\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`InUse` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`IsBroken` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`IsBundle` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`IsDigest` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`IsEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`IsExpired` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`IsHidden` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`IsLatest` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`IsQuarantined` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`IsSuperseded` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read, not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`IsUserDefined` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`LastModifiedBy` Data type: `String`

Access type: Read-only

Qualifiers: \[SizeLimit\("512"\), read, not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String Array`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`LocalizedDescription` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`LocalizedDisplayName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`LocalizedEulas` Data type: `SMS_CI_LocalizedEulas Array`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`LocalizedInformation` Data type: `SMS_CI_LocalizedProperties Array`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`LocalizedInformativeURL` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`LocalizedPropertyLocaleID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`ModelID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: \[unique,not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`PermittedUses` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`PlatformCategoryInstance_UniqueIDs` Data type: `String Array`

Access type: Read/Write

Qualifiers: none

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`PlatformType` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[bitmap, bitvalues, read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`SDMPackageLocalizedData` Data type: `SMS_SDMPackageLocalizedData Array`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`SDMPackageVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[not\_null\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`SDMPackageXML` Data type: `String`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`SecuredScopeNames` Data type: `String Array`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read/Write

Qualifiers: \[SizeLimit\("3"\)\]

See [SMS\_SettingsDefinitionBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_settingsdefinitionbase-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes)
