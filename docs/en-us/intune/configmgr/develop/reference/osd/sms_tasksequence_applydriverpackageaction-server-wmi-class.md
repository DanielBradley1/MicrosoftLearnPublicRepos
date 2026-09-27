<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_applydriverpackageaction-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_TaskSequence\_ApplyDriverPackageAction server WMI class

The `SMS_TaskSequence_ApplyDriverPackageAction` WMI class is an SMS Provider server class in Configuration Manager. It represents an action used in a task sequence to make all device drivers in a driver package available for use by Windows setup.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```MOF
Class SMS_TaskSequence_ApplyDriverPackageAction : SMS_TaskSequence_Action
{
        String BootCriticalContentUniqueID;
        String BootCriticalDriverID;
        String BootCriticalHardwareComponent;
        String BootCriticalID;
        String BootCriticalINFFile;
        SMS_TaskSequence_Condition Condition;
        Boolean ContinueOnError;
        String Description;
        String DriverPackageID;
        Boolean Enabled;
        String Name;
        Boolean Recurse;
        String SupportedEnvironment;
        UInt32 Timeout;
        Boolean UnsignedDriver;
};
```

## Methods

The `SMS_TaskSequence_ApplyDriverPackageAction` class doesn't define any methods.

## Properties

### `BootCriticalContentUniqueID`

Data type: `String`

Access type: Read/Write

Qualifiers: `[RequiredIfNotNull]`

The unique ID of the content associated a boot-critical mass storage device driver. If this ID isn't specified, no mass-storage device driver is installed. The driver content can be obtained from the [SMS\_CIToContent server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_citocontent-server-wmi-class) where the **CI\_ID** property matches the driver ID. The default value is `null`.

Note

This property is required if **BootCriticalDriverID** is set.

### `BootCriticalDriverID`

Data type: `String`

Access type: Read/Write

Qualifiers: `[CommandLineArg(2)]`

Optional ID specified by the **CI\_UniqueID** property of the [SMS\_Driver server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object to install for a boot-critical mass storage device driver. The default value is `null`.

### `BootCriticalHardwareComponent`

Data type: `String`

Access type: Read/Write

Qualifiers: `[RequiredIfNotNull]`

Hardware component used if a boot-critical mass storage device driver is being installed. The default value is `null`.

Note

This property is required if **BootCriticalDriverID** is set.

### `BootCriticalID`

Data type: `String`

Access type: Read/Write

Qualifiers: `[RequiredIfNotNull]`

The boot-critical ID of the mass-storage device driver to be installed. The default value is `null`. This ID is listed in the "scsi" section of the device driver Txtsetup.oem file.

Note

This property is required if **BootCriticalDriverID** is set.

### `BootCriticalINFFile`

Data type: `String`

Access type: Read/Write

Qualifiers: `[RequiredIfNotNull]`

The INF file of a boot-critical mass-storage device driver to be installed. The default value is `null`.

Note

This property is required if **BootCriticalDriverID** is set.

### `Condition`

Data type: `SMS_TaskSequence_Condition`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `ContinueOnError`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Description`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("0-255")]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `DriverPackageID`

Data type: `String`

Access type: Read/Write

Qualifiers: `[CommandLineArg(1), TaskSequencePackage, Not_Null]`

ID of the driver package to install. This value is indicated by the **PackageID** property of the specific [SMS\_DriverPackage server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driverpackage-server-wmi-class) object.

### `Enabled`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Name`

Data type: `String`

Access type: Read/Write

Qualifiers: `[AllowedLen("1-100")]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `Recurse`

Data type: `Boolean`

Access type: Read/write

Values:

- `false` \(default\): Use the list of drivers from the driver package.
- `true`: Run DISM once to recurse on the entire driver package folder.

### `SupportedEnvironment`

Data type: `String`

Access type: Read/Write

Qualifiers: `[Not_Null:ToInstance]`

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

The default value for this class is WinPE.

### `Timeout`

Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

For more information, see [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).

### `UnsignedDriver`

Data type: `Boolean`

Access type: Read/Write

Qualifiers: `[Not_Null, VariableName("OSDAllowUnsignedDriver")]`

Set `true` to configure Windows to allow unsigned device drivers to be installed. The default value is `false`.

Note

This property is required by the action. However, it's deprecated and not used by modern OS versions.

## Remarks

Class qualifiers for this class include:

```
[CommandLine("osddriverclient.exe /install:%1 \<?2:\\"/bootcritical:%%OSDApplyDriverBootCriticalContentUniqueID%%,%%OSDApplyDriverBootCriticalINFFile%%,%%OSDApplyDriverBootCriticalHardwareComponent%%,%%OSDApplyDriverBootCriticalID%%\\">/unsigned:%%OSDAllowUnsignedDriver%%"),ActionCategory{"Drivers,2,6"},ActionUI{"AdminUI.TaskSequenceEditor.dll", "Microsoft.ConfigurationManagement.AdminConsole.TaskSequenceEditor", "ApplyDriverPackageControl", "TaskSequenceOptionControl"}, VariablePrefix("OSDApplyDriver")]
```

For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager class and property qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

- [SMS\_Driver server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class)
- [SMS\_DriverPackage server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driverpackage-server-wmi-class)
- [SMS\_TaskSequence\_Action server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class)
