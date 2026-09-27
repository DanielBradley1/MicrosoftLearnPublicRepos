<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_softwareproduct-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_G\_System\_SoftwareProduct Server WMI Class

The `SMS_G_System_SoftwareProduct` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that provides software product information for software files that contain resource strings.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_G_System_SoftwareProduct : SMS_G_System
{
     String CompanyName;
     UInt32 ProductId;
     UInt32 ProductLanguage;
     String ProductName;
     String ProductVersion;
     UInt32 ResourceID;
};
```

## Methods

The `SMS_G_System_SoftwareProduct` class doesn't define any methods.

## Properties

`CompanyName` Data type: **String**

Access type: Read/Write

Qualifiers: none

Name of the software manufacturer taken from the company name resource string. This name can be universally changed by using the rules that are defined in [SMS\_SoftwareConversionRules Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_softwareconversionrules-server-wmi-class).

`ProductId` Data type: **UInt32**

Access type: Read/Write

Qualifiers: \[key\]

Configuration Manager-supplied ID that uniquely identifies the product. The property links this product with the software file information contained in an [SMS\_G\_System\_SoftwareFile Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_softwarefile-server-wmi-class) object.

`ProductLanguage` Data type: **UInt32**

Access type: Read/Write

Qualifiers: \[Subtype\("Locale ID"\)\]

Language taken from the language resource string.

`ProductName` Data type: **String**

Access type: Read/Write

Qualifiers:\[DefaultOrder\("ASC"\)\]

Value of the product name resource string.

`ProductVersion` Data type: **String**

Access type: Read/Write

Qualifiers: none

Value of the product version resource string.

`ResourceID` Data type: **UInt32**

Access type: Read/Write

Qualifiers: \[key\]

See [SMS\_G\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class).

## Remarks

There are no special class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

The Software Inventory Agent inventories files identified in the site control file. To identify the files to inventory, the agent:

1. Queries the site control [SMS\_SCI\_ClientComp Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) objects for items having the value "Software Inventory Agent" for the `ClientComponentName` property.
2. Loops through the embedded property list. When the value for `PropertyName` is "Inventoriable Types", the agent updates the comma-delimited list of file names \(including extensions\) in the `Value2` property. When the value for `PropertyName` is "Inventory Schedule", the agent updates the interval string in the `Value2` property. For information about creating an interval string, see the example for the [WriteToString Method in Class SMS\_ScheduleMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/writetostring-method-in-class-sms_schedulemethods) method. When the value for `PropertyName` is "Report Options", the agent updates the reporting options value in the `Value` property, specifying at least one reporting option for the software inventory to be collected. The following table lists the reporting options.
   | Reporting option | Description |
   | --- | --- |
   | Product version information. Bit 0. | Inventories products that contain company and product resource information. |
   | Files associated with known products. Bit 1. | Inventories files associated with products that contain company and product resource information. For example, Wwintl32.dll is inventoried because it's associated with Microsoft Word.  <br>  <br>Set this bit only if the product version information reporting option is selected. |
   | Files not associated with known products. Bit 2. | Inventories files that don't include company and product resource information \(unknown files\). |
3. For newly added inventory types, adds entries to the following `Path`, `Subdirectories`, and `Exclude` embedded property lists.

   Updates the site control file. For more information, see [About the site control file](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file).

Note

Collecting inventory information for some files, for example, DLL files, can generate a large volume of network traffic and substantially increase the size of the Configuration Manager database. For this reason, test any changes you make in a test environment before implementing them in a production environment.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_G\_System Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system-server-wmi-class) [SMS\_SoftwareConversionRules Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_softwareconversionrules-server-wmi-class) [SMS\_G\_System\_SoftwareFile Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_g_system_softwarefile-server-wmi-class) [About the site control file](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file)
