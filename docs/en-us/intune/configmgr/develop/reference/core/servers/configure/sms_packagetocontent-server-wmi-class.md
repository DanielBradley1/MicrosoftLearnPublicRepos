<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagetocontent-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_PackageToContent Server WMI Class

The `SMS_PackageToContent` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that relates a Configuration Manager package to its content.

## Syntax

```
Class SMS_PackageToContent : SMS_BaseClass
{
      SInt32 ContentID;
      String ContentSubFolder;
      String ContentUniqueID;
      SInt32 ContentVersionInPkg;
      SInt32 MinPackageVersion;
      String PackageID;
      UInt32 PackageType;
      UInt32 SecuredTypeID;
      String SecureObjectID;
};
```

## Methods

The following table lists the methods in `SMS_PackageToContent`.

| Method | Description |
| --- | --- |
| [IsContentValid Method in Class SMS\_PackageToContent](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/iscontentvalid-method-in-class-sms_packagetocontent) | Determines if the package content is valid. |

## Properties

`ContentID` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[key, Not\_null\]

The value of the `ContentID` property of the package.

`ContentSubFolder` Data type: `String`

Access type: Read/Write

Qualifiers: \[Not\_null\]

The name of the subfolder in the package source folder that contains the files for the content.

`ContentUniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[read, Not\_null\]

The unique ID for the content.

`ContentVersionInPkg` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[Not\_null\]

The version of the content in the package.

`MinPackageVersion` Data type: `SInt32`

Access type: Read/Write

Qualifiers: \[Not\_null\]

The minimum package version in which the content appears.

`PackageID` Data type: `String`

Access type: Read/Write

Qualifiers: \[key, Not\_null\]

Configuration Manager-specific ID of the package.

`PackageType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[enumeration\]

The type of the package. Possible values are:

| Value | Description |
| --- | --- |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 4 | PKG\_TYPE\_TASK\_SEQUENCE |
| 5 | PKG\_TYPE\_SWUPDATES |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |

`SecuredTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

Secured type of related package.

`SecureObjectID` Data type: `String`

Access type: Read/Write

Qualifiers: None

Secure object ID. For app, it is model name. For others, it is package ID.

## Remarks

Class qualifiers for this class include:

- Secured
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Your application can query this class to get the list of contents contained by a package or the list of packages that contain specified content.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
