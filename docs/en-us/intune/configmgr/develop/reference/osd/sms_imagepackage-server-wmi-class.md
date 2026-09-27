<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imagepackage-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_ImagePackage Server WMI Class

The `SMS_ImagePackage` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that serves as the unit of distribution for image source files that are used to deploy a valid operating system, for example, Windows 10, in WIM format to a client computer.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ImagePackage : SMS_PackageBaseclass
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
      String ImageDiskLayout;
      String ImageProperty;
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
      String PackageID;
      UInt32 PackageType;
      UInt32 PkgFlags;
      UInt32 PkgSourceFlag;
      String PkgSourcePath;
      String PreferredAddressType;
      UInt32 Priority;
      Boolean RefreshPkgSourceFlag;
      SMS_ScheduleToken RefreshSchedule[];
      String SecuredScopeNames[];
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

The following table shows the methods in `SMS_ImagePackage`.

| Method | Description |
| --- | --- |
| [AddChangeNotification Method in Class SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/addchangenotification-method-in-class-sms_imagepackage) | Adds an image package change notification. |
| [AddDistributionPoints Method in Class SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/adddistributionpoints-method-in-class-sms_imagepackage) | Adds the distribution points for the package. |
| [GetImageProperties Method in Class SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getimageproperties-method-in-class-sms_imagepackage) | Reads all image properties from the specified WIM file to an XML string. |
| [RefreshPkgSource Method in Class SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/refreshpkgsource-method-in-class-sms_imagepackage) | Refreshes the package source at all distribution points, when the package properties have not changed. |
| [ReloadImageProperties Method in Class SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_imagepackage) | Reloads image properties from source WIM file and updates the database. |
| [RunOfflineServicingManager Method in Class SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/runofflineservicingmanager-method-in-class-sms_imagepackage) | Triggers the offline servicing manager to run as soon as possible. |
| [SetSourceSite Method in Class SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsourcesite-method-in-class-sms_imagepackage) | Sets the code of the source site for the image package. |
| [Unlock Method in Class SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/unlock-method-in-class-sms_imagepackage) | Sets the source site to the current site, unlocking the image package. |

## Properties

`ActionInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`AlternateContentProviders` Data type: `String`

Access type: Read/Write

Qualifiers: \[large, lazy\]

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

`ImageDiskLayout` Data type: `String`

Access type: Read-only

Qualifiers: \[lazy, read\]

An XML string of disk drive layout information about the source WIM image. The default value is "".

`ImageProperty` Data type: `String`

Access type: Read/Write

Qualifiers: \[lazy\]

An XML string of image metadata for the source WIM file. The default value is "".

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

`PackageID` Data type: `String`

Access type: \[key\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PackageType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

For this class, the package type is PKG\_TYPE\_IMAGE \(257\).

`PkgFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PkgSourceFlag` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PkgSourcePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PreferredAddressType` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`Priority` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`RefreshPkgSourceFlag` Data type: `Boolean`

Access type: Read/Write

Qualifiers: \[lazy\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`RefreshSchedule` Data type: `SMS_ScheduleToken` Array

Access type: \[max\(15\), lazy, ResID\(725\), ResDLL\("SMS\_RSTT.dll"\)\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SecuredScopeNames` Data type: `String` Array

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

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

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

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

## Remarks

Class qualifiers for this class include:

- Secured
- Icon\("Package.ico"\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  To get started using this class, see How to Add an Operating System Image Package in Configuration Manager.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
