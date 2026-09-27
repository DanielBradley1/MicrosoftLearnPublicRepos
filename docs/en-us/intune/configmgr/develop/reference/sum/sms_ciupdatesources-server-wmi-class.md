<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_ciupdatesources-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CIUpdateSources Server WMI Class

The `SMS_CIUpdateSources` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that provides information on all the update sources associated with an [SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class) object.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CIUpdateSources : SMS_BaseClass
{
    UInt32 CI_ID;
    DateTime DateCreated;
    DateTime DateModified;
    UInt32 MinSourceVersion;
    String ModelName;
    UInt32 UpdateSource_ID;
};
```

## Methods

The `SMS_CIUpdateSources` class does not define any methods.

## Properties

`CI_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

Unique ID of the configuration item corresponding to the software update. This ID is unique only for the site. The ID is defined by the `CI_ID` property of SMS\_ConfigurationItemBaseClass Server WMI Class.

`DateCreated` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

Date and time when the configuration was created.

`DateModified` Data type: `DateTime`

Access type: Read/Write

Qualifiers: None

The last date and time when the configuration item was modified.

`MinSourceVersion` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Minimum version of the source in which the update was found.

`ModelName` Data type: `String`

Access type: Read/Write

Qualifiers: None

See [SMS\_ConfigurationItemLatestBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitemlatestbaseclass-server-wmi-class).

`UpdateSource_ID` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

The ID of the software update source. Supported sources are Windows Server Update Services \(WSUS\) and ITMU/Offline Catalog. For more information, see [SMS\_SoftwareUpdateSource Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatesource-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  Your application uses this class in synchronizing software update metadata so that correct information can be obtained from a source during software update deployment.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class) [SMS\_SoftwareUpdateSource Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatesource-server-wmi-class) [About software update deployments](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-deployments)
