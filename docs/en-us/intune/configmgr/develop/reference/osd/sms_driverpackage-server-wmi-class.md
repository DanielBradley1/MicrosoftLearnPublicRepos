<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driverpackage-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DriverPackage Server WMI Class

The `SMS_DriverPackage` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents the package that is the unit of distribution of program binaries with which one or more device drivers are associated.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DriverPackage : SMS_PackageBaseclass
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
      String SecuredScopeNames;
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

The following table shows the methods in `SMS_DriverPackage`.

| Method | Description |
| --- | --- |
| [AddChangeNotification Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/addchangenotification-method-in-class-sms_driverpackage) | Adds a driver package change notification. |
| [AddDistributionPoints Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/adddistributionpoints-method-in-class-sms_driverpackage) | Adds the distribution points for the driver package. |
| [AddDriverContent Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/adddrivercontent-method-in-class-sms_driverpackage) | Adds a driver to the package and replicates to distribution points. |
| [CheckSourceFolder Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/checksourcefolder-method-in-class-sms_driverpackage) | Checks the source folder for this driver package. |
| [RebuildPackage Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/rebuildpackage-method-in-class-sms_driverpackage) | Restores the contents for this driver package. |
| [RefreshPkgSource Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/refreshpkgsource-method-in-class-sms_driverpackage) | Refreshes the package source at all distribution points, when the package properties have not changed. |
| [RemoveDriverContent Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/removedrivercontent-method-in-class-sms_driverpackage) | Removes the specified driver from the driver package. |
| [SetSourceSite Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsourcesite-method-in-class-sms_driverpackage) | Sets the code of the source site for the driver package. |
| [Unlock Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/unlock-method-in-class-sms_driverpackage) | Sets the source site to the current site, unlocking the driver package. |
| [ValidateNewPackageSource Method in Class SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/validatenewpackagesource-method-in-class-sms_driverpackage) | Validates the new package source location by verifying the content. |

## Properties

`ActionInProgress` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`AlternateContentProviders` Data type: `String`

Access type: Read/Write

Qualifiers: \[large, lazy\]

Not used for this class.

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

Access type: Read/Write

Qualifiers: None

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

`PackageSize` Data type: `UInt32`

Access type: Read

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PackageType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

For this class, the package type is PKG\_TYPE\_DRIVER \(3\).

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

The UNC path to the driver package.

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

Access type:

Qualifiers: \[max\(15\), lazy\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SecuredScopeNames` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`SedoObjectVersion` Data type: `String`

Access type: Read/Write

Qualifiers: None

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

  Your application uses this class to create a driver package that contains the content for one or more device drivers. When the application adds a new driver, the content is added to the driver package share. The driver package can then be copied to a distribution point so that computers can install the drivers. For more information, see How to Create a Driver Package for a Windows Driver in Configuration Manager.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
