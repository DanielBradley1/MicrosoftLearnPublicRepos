<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_osdeploymentkitwinpeoptionalcomponent-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_OSDeploymentKitWinPEOptionalComponent Server WMI Class

The `SMS_OSDeploymentKitWinPEOptionalComponent` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that Maps Assessment and Deployment Kit \(ADK\) versions to supported optional components.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_OSDeploymentKitWinPEOptionalComponent : SMS_WinPEOptionalComponentInfo
{
    String Architecture;
    String DependentComponentNames[];
    UInt32 DependentIds[];
    String DeploymentKitVersion;
    Boolean IsRequired;
    UInt32 LanguageID;
    String Name;
    String RelativePath;
    UInt64 Size;
    UInt32 UniqueID;
};
```

## Methods

The `SMS_OSDeploymentKitWinPEOptionalComponent` class does not define any methods.

## Properties

`Architecture` Data type: `String`

Access type: Read

Qualifiers: none

See [SMS\_WinPEOptionalComponentInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class).

`DependentComponentNames` Data type: `String Array`

Access type: Read

Qualifiers: none

See [SMS\_WinPEOptionalComponentInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class).

`DependentIds` Data type: `UInt32 Array`

Access type: Read

Qualifiers: none

See [SMS\_WinPEOptionalComponentInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class)>.

`DeploymentKitVersion` Data type: `String`

Access type: Read

Qualifiers: \[not\_null\]

The version of the deployment kit with which this property is associated.

`IsRequired` Data type: `Boolean`

Access type: Read

Qualifiers: none

See [SMS\_WinPEOptionalComponentInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class).

`LanguageID` Data type: `Unit32`

Access type: Read

Qualifiers: \[key\]

See [SMS\_WinPEOptionalComponentInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class).

`Name` Data type: `String`

Access type: Read

Qualifiers: none

See [SMS\_WinPEOptionalComponentInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class).

`RelativePath` Data type: `String`

Access type: Read

Qualifiers: none

See [SMS\_WinPEOptionalComponentInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class).

`Size` Data type: `UInt34`

Access type: Read

Qualifiers: none

See [SMS\_WinPEOptionalComponentInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class).

`UniqueID` Data type: `UInt32`

Access type: Read

Qualifiers: \[key\]

See [SMS\_WinPEOptionalComponentInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_winpeoptionalcomponentinfo-server-wmi-class).

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
