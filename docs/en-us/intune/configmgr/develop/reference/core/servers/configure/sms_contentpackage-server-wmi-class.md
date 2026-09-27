<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_contentpackage-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ContentPackage Server WMI Class

The `SMS_ContentPackage` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the content package.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ContentPackage : SMS_PackageBaseclass
{
    UInt32 ActionInProgress;
    String AlternateContentProviders;
    String Description;
    UInt8 ExtendedData[];
    UInt32 ExtendedDataSize;
    UInt32 ForcedDisconnectDelay;
    Boolean ForcedDisconnectEnabled;
    UInt32 ForcedDisconnectNumRetries;
    UInt8 Icon[];
    UInt32 IconSize;
    Boolean IgnoreAddressSchedule;
    UInt8 ISVData[];
    UInt32 ISVDataSize;
    String Language;
    DateTime LastRefreshTime;
    String LocalizedCategoryInstanceNames[];
    String Manufacturer;
    String MIFFilename;
    String MIFName;
    String MIFPublisher;
    String MIFVersion;
    String Name;
    UInt32 NumOfPrograms;
    UInt32 ObjectTypeID;
    String PackageID;
    UInt32 PackageSize;
    UInt32 PackageType;
    UInt32 PkgFlags;
    UInt32 PkgSourceFlag;
    String PkgSourcePath;
    String PreferredAddressType;
    UInt32 Priority;
    Boolean RefreshPkgSourceFlag;
    SMS_ScheduleToken RefreshSchedule[];
    String SecuredScopeNames[];
    String SecurityKey;
    String SedoObjectVersion;
    String ShareName;
    UInt32 ShareType;
    DateTime SourceDate;
    String SourceSite;
    UInt32 SourceVersion;
    String StoredPkgPath;
    UInt32 StoredPkgVersion;
    String Version;
};
```

## Methods

The following table lists the methods in the `SMS_ContentPackage` class.

| Method | Description |
| --- | --- |
| [AddChangeNotification Method in Class SMS\_ContentPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/addchangenotification-method-in-class-sms_contentpackage) | Adds a package change notification. |
| [AddContent Method in Class SMS\_ContentPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/addcontent-method-in-class-sms_contentpackage) | Adds a set of contents to this content package |
| [AddDistributionPointGroup Method in Class SMS\_ContentPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/adddistributionpointgroup-method-in-class-sms_contentpackage) | Adds a distribution point group for the content package. |
| [AddDistributionPoints Method in Class SMS\_ContentPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/adddistributionpoints-method-in-class-sms_contentpackage) | Adds the distribution points for the content package. |
| [Commit Method in Class SMS\_ContentPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/commit-method-in-class-sms_contentpackage) | Called when all the contents have been added to the content package to start package processing. |
| [RemoveContent Method in Class SMS\_ContentPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/removecontent-method-in-class-sms_contentpackage) | Removes the content for the given ContentID from the package. |
| [RefreshPkgSource Method in Class SMS\_ContentPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/refreshpkgsource-method-in-class-sms_contentpackage) | Causes a refresh of the package source. |
| [Unlock Method in Class SMS\_ContentPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/unlock-method-in-class-sms_contentpackage) | Sets the source site to the current site, unlocking the package. **Important:** This method is obsolete. |
| [SetSourceSite Method in Class SMS\_ContentPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/setsourcesite-method-in-class-sms_contentpackage) | Sets the code of the source site for the package. |

## Properties

`ActionInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[enumeration, read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`AlternateContentProviders` Data type: `String`

Access type: Read/Write

Qualifiers: \[large, lazy, resdll, resid\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Description` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ExtendedData` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: \[large, lazy\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ExtendedDataSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ForcedDisconnectDelay` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ForcedDisconnectEnabled` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ForcedDisconnectNumRetries` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Icon` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: \[large\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`IconSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`IgnoreAddressSchedule` Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ISVData` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: \[large, lazy\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ISVDataSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Language` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`LastRefreshTime` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`LocalizedCategoryInstanceNames` Data type: `String` Array

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Manufacturer` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`MIFFilename` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`MIFName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`MIFPublisher` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`MIFVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`NumOfPrograms` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ObjectTypeID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

The security type of the content.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PackageSize` Data type: `UInt32`

Access type: Read

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PackageType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[enumeration\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PkgFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PkgSourceFlag` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[enumeration\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PkgSourcePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PreferredAddressType` Data type: `String`

Access type: Read/Write

Qualifiers: \[stringenumeration\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[enumeration\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`RefreshPkgSourceFlag` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`RefreshSchedule` Data type: `SMS_ScheduleToken` Array

Access type: Read/Write

Qualifiers: \[lazy, max\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SecuredScopeNames` Data type: `String` Array

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SecurityKey` Data type: `String`

Access type: Read/Write

Qualifiers: None

The security key of the content. Content may security by app or package.

`SedoObjectVersion` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ShareName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`ShareType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[enumeration\]

Specifies whether the package uses the common package share on the distribution point or a custom share.

`SourceDate` Data type: `DateTime`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SourceSite` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SourceVersion` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`StoredPkgPath` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`StoredPkgVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Version` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
