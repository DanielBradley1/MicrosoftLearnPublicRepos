<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cicontentfiles-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CIContentFiles Server WMI Class

The `SMS_CIContentFiles` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that lists all files associated with the content of a specific [SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class) object.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CIContentFiles : SMS_BaseClass
{
    String CI_UniqueID;
    UInt32 ContentID;
    String FileHash;
    String FileName;
    SInt64 FileSize;
    String FileVersion;
    String ImportPath;
    Boolean IsSigned;
    UInt32 LanguageID;
    String ModelName;
    UInt32 ObjectTypeID;
    String SourceURL;
};
```

## Methods

The `SMS_CIContentFiles` class does not define any methods.

## Properties

`CI_UniqueID` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ContentID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read, key, Not\_null\]

ID for the software update content. See the `ContentID` property of [SMS\_CIToContent Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class).

`FileHash` Data type: `String`

Access type: Read-only

Qualifiers: \[read, Not\_null\]

The file hash.

`FileName` Data type: `String`

Access type: Read-only

Qualifiers: \[read, key, Not\_null\]

File name, including the subdirectory path under the root directory.

`FileSize` Data type: `SInt64`

Access type: Read-only

Qualifiers: \[read, Not\_null\]

The size of the file.

`FileVersion` Data type: `String`

Access type: Read-only

Qualifiers: \[read, Not\_null\]

The file version.

`ImportPath` Data type: `String`

Access type: Read-only

Qualifiers: \[read, Not\_null\]

The file location \(including file name\) relative to the import root.

`IsSigned` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read, Not\_null\]

`true` if the software update content is signed.

`LanguageID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read\]

The language attribute of the file.

`ModelName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`ObjectTypeID` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[read, Not\_null\]

Secured object class ID. Possible values are listed below.

| ID value | Object type |
| --- | --- |
| 0 | PKG\_TYPE\_REGULAR |
| 3 | PKG\_TYPE\_DRIVER |
| 4 | PKG\_TYPE\_TASK\_SEQUENCE |
| 5 | PKG\_TYPE\_SWUPDATES |
| 6 | PKG\_TYPE\_DEVICE\_SETTING |
| 8 | PKG\_CONTENT\_PACKAGE |
| 257 | PKG\_TYPE\_IMAGE |
| 258 | PKG\_TYPE\_BOOTIMAGE |
| 259 | PKG\_TYPE\_OSINSTALLIMAGE |
| 512 | APPLICATION |

`SourceURL` Data type: `String`

Access type: Read-only

Qualifiers: \[read, Not\_null\]

URL where the source for the content file is located.

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)
- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  This class is used to determine update files to download for a particular update, for example, when there are different locales associated with the update. When using this class, first identify which contents need to be downloaded by querying [SMS\_CIToContent Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class) and obtain the list of `ContentID` properties matching the specific language criteria. Given the list, you can then obtain the associated download URL and the related properties for the content files from `SMS_CIContentFiles`.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class) [SMS\_CIToContent Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class)
