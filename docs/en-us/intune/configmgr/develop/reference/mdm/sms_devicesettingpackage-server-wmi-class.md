<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/sms_devicesettingpackage-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_DeviceSettingPackage Server WMI Class

The `SMS_DeviceSettingPackage` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class that represents a device setting package in the database.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_DeviceSettingPackage : SMS_PackageBaseclass
{
      UInt32 ActionInProgress;
      String AlternateContentProviders;
      String Description;
      String DeviceSettingItemUniqueIDs[];
      String DeviceSettingPackageXML;
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
      String PlatformType;
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

The following table shows the methods in `SMS_DeviceSettingPackage`.

| Method | Description |
| --- | --- |
| [AddChangeNotification Method in Class SMS\_DeviceSettingPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/addchangenotification-method-in-class-sms_devicesettingpackage) | Adds a device setting package change notification. |
| [AddDistributionPoints Method in Class SMS\_DeviceSettingPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/adddistributionpoints-method-in-class-sms_devicesettingpackage) | Adds the distribution points for the device setting package. |
| [RefreshPkgSource Method in Class SMS\_DeviceSettingPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/refreshpkgsource-method-in-class-sms_devicesettingpackage) | Refreshes the package source at all distribution points, when the package properties have not changed. |
| [SetSourceSite Method in Class SMS\_DeviceSettingPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/setsourcesite-method-in-class-sms_devicesettingpackage) | Sets the code of the source site for the device setting package. |
| [Unlock Method in Class SMS\_DeviceSettingPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/unlock-method-in-class-sms_devicesettingpackage) | Sets the source site to the current site, unlocking the device setting package. |

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

`DeviceSettingItemUniqueIDs` Data type: `String` Array

Access type: Read/Write

Qualifiers: \[lazy\]

GUIDs or unique IDs of the device settings contained in the package.

`DeviceSettingPackageXML` Data type: `String`

Access type: Write-only

Qualifiers: None

User interface used to provide device setting package XML through this property. The default value is "".

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

`PkgFlags` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[bits\]

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PkgSourceFlag` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

For this class, the flag setting is STORAGE\_DIRECT \(2\).

`PkgSourcePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

`PlatformType` Data type: `String`

Access type: Read/Write

Qualifiers: None

The type of platform to which the device setting package applies. The default value is "".

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

Access type: \[max\(15\), lazy\]

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

Qualifiers: \[read,\]

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

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Mobile device setting packages use programs, distribution points, and advertisements to collections to distribute their content.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Device Management Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/device-management-server-wmi-classes) [SMS\_PackageBaseclass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class)
