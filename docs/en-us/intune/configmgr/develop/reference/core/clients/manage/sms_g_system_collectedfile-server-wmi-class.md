<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_collectedfile-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_System\_CollectedFile Server WMI Class

The `SMS_G_System_CollectedFile` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that contains information about a file copied from the client computer to the site server.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_CollectedFile : SMS_G_System
{
     DateTime CollectionDate;
     UInt8 FileData[];
     String FileName;
     String FilePath;
     UInt32 FileSize;
     DateTime FileModifyDate;
     String LocalFilePath;
     DateTime ModifiedDate;
     UInt32 ResourceID;
     UInt32 RevisionID;
};
```

## Methods

The `SMS_G_System_CollectedFile` class does not define any methods.

## Properties

`CollectionDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time the file was collected from the client computer.

`FileData` Data type: `UInt8` Array

Access type: Read/Write

Qualifiers: \[lazy\]

Contents of the file.

`FileName` Data type: `String`

Access type: Read/Write

Qualifiers: \[DefaultOrder\("ASC"\)\]

Name and file name extension of the file.

`FilePath` Data type: `String`

Access type: Read/Write

Qualifiers: \[key\]

Path to the file on the client computer.

`FileSize` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Size of the file, in bytes.

`LocalFilePath` Data type: `String`

Access type: Read/Write

Qualifiers: None

Path to the file on the site server.

`ModifiedDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time the file was last modified.

`ResourceID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_G\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class).

`RevisionID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Revision ID that increments each time an inventory is taken to identify the number of times the file has been inventoried. The file is only inventoried when it has changed.

`FileModifyDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time the file was last modified.

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

The Software Inventory Agent collects files identified in the site control file. To identify the files to collect, the agent:

1. Queries the site control [SMS\_SCI\_ClientComp Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) objects for items having the value "Software Inventory Agent" for the `ClientComponentName` property.
2. Loops through the embedded property list. When the value for `PropertyName` is "Collectable Files", the agent updates the comma-delimited list of file names \(including extensions\) in the `Value2` property. When the value for `PropertyName` is "Max Collected File Size", the agent sets a maximum size, in megabytes, for the files that Configuration Manager collects from the client, for that query, during each software inventory cycle.
3. For any new collectable file added, adds an entry to each of the embedded property lists Collectable File Path, Collectable File Subdirectories, Collectable File Exclude, and Collectable File Max Size.
4. Updates the site control file. For more information, see [About the site control file](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file).

Note

Collecting files from clients can generate a large volume of network traffic and require extensive storage space. For this reason, you should test any changes you make in a test environment before implementing them in a production environment.

Collected files are deleted on a schedule if the Delete Aged Collected Files database maintenance task is set to `true` in the Configuration Manager console. You can also enable this task and set the schedule by updating the site control file. The site control item is an instance of [SMS\_SCI\_SQLTask Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_sqltask-server-wmi-class) and the `TaskName` value is "Delete Aged Collected Files".

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_G\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class) [About the site control file](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file)
