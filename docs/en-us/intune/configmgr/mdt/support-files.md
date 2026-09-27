<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/mdt/support-files -->
<!-- Sitemap-Last-Modified: 2024-02-12 -->

# Support Files

The utilities and scripts used in LTI and ZTI deployments reference external configuration files to determine the process steps and configuration settings used during the deployment process.

The following information is provided for each utility:

- **Name**. Specifies the name of the file
- **Description**. Provides a description of the purpose of the file
- **Location**. Indicates the folder where the file can be found; in the information for the location, the following variables are used:

  - **program\_files**. This variable points to the location of the Program Files folder on the computer where MDT is installed.
  - **distribution**. This variable points to the location of the Distribution folder for the deployment share.
  - **platform**. This variable is a placeholder for the operating system platform \(x86 or x64\).

## ApplicationGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## Applications.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## BootStrap.ini

The configuration file used when the target computer is not able to connect to the appropriate deployment share. This situation occurs in the New Computer and the Replace Computer scenarios.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## CustomSettings.ini

The primary configuration file for the MDT processing rules used in all scenarios.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## Deploy.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *program\_files*\\Microsoft Deployment Toolkit\\Control |

## DriverGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## Drivers.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | Description |
| --- | --- |
| **Location** | *distribution*\\Control |

## LinkedDeploymentShares.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Scripts |

## ListOfLanguages.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Scripts |

## MediaGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Scripts |

## Medias.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Scripts |

## OperatingSystemGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## OperatingSystems.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## PackageGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## Packages.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## SelectionProfileGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## SelectionProfiles.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## ServerManager.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *program\_files*\\Microsoft Deployment Toolkit\\Bin |

## Settings.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## TaskSequenceGroups.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## TaskSequences.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control |

## TS.xml

Note

This XML file is managed by MDT and should not require modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Control\\*task\_sequence\_id* |

Note

*Task\_sequence\_id* is a placeholder for the task sequence ID that was assigned to each task sequence when it was created in the Task Sequences node in the Deployment Workbench.

## Wimscript.ini

This .ini file is an ImageX configuration file that contains the list of folders and files that will be excluded from an image. It is referenced by ImageX during the LTI Capture Phase.

For assistance with customizing this file, see the section, "Create an ImageX Configuration File," in the *Windows Preinstallation Environment \(Windows PE\) User's Guide*.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Tools\\*platform* |

## ZTIBIOSCheck.xml

This XML file contains metadata about BIOSes for target computers. This file is edited manually and is read by [ZTIBIOSCheck.wsf](https://learn.microsoft.com/en-us/intune/configmgr/mdt/scripts#ztibioscheckwsf). Extract the necessary information from a target computer to create an entry in this XML file using the Microsoft Visual Basic® Scripting Edition \(VBScript\) program \(ZTIBIOS\_Extract\_Utility.vbs\) that is embedded in this XML file.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Scripts |

## ZTIConfigure.xml

This XML file is used by the [ZTIConfigure.wsf](https://learn.microsoft.com/en-us/intune/configmgr/mdt/scripts#zticonfigurewsf) script to translate property values \(specified earlier in the deployment process\) to configure settings in the Unattend.xml file. This file is already customized to make the appropriate translations and should not require further modification.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Scripts |

## ZTIGather.xml

Note

This XML file is preconfigured and should not require modification. Define custom properties in the CustomSettings.ini file or the MDT DB.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Scripts |

## ZTIUserState\_config.xml

This XML file is used by the [ZTIUserState.wsf](https://learn.microsoft.com/en-us/intune/configmgr/mdt/scripts#ztiuserstatewsf) script as a default USMT configuration file. This file is used by default if no custom configuration file is specified by the [USMTConfigFile](https://learn.microsoft.com/en-us/intune/configmgr/mdt/properties#usmtconfigfile) property. See the [Config.xml File](https://learn.microsoft.com/en-us/windows/deployment/usmt/usmt-configxml-file) topic in the USMT documentation for more information on syntax and use.

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Scripts |

## ZTITatoo.mof

This .mof file, when imported into the WMI repository of the target computer using Mofcomp.exe, creates the **Microsoft\_BDD\_Info** WMI class. This class contains deployment-related information, such as:

- DeploymentMethod
- DeploymentType
- DeploymentTimestamp
- BuildID
- BuildName
- BuildVersion
- OSDPackageID
- OSDProgramName
- OSDAdvertisementID
- TaskSequenceID
- TaskSequenceName
- TaskSequenceVersion

| **Value** | **Description** |
| --- | --- |
| **Location** | *distribution*\\Scripts |

## Related articles

- [Task Sequence Steps](https://learn.microsoft.com/en-us/intune/configmgr/mdt/task-sequence-steps).
- [Properties](https://learn.microsoft.com/en-us/intune/configmgr/mdt/properties).
- [Scripts](https://learn.microsoft.com/en-us/intune/configmgr/mdt/scripts).
- [Utilities](https://learn.microsoft.com/en-us/intune/configmgr/mdt/utilities).
- [MDT Windows PowerShell Cmdlets](https://learn.microsoft.com/en-us/intune/configmgr/mdt/mdt-windows-powershell-cmdlets).
- [Tables and Views in the MDT DB](https://learn.microsoft.com/en-us/intune/configmgr/mdt/tables-views-mdt-db).
- [Windows 7 Feature Dependency Reference](https://learn.microsoft.com/en-us/intune/configmgr/mdt/windows-7-feature-dependency).
- [UDI Reference](https://learn.microsoft.com/en-us/intune/configmgr/mdt/udi-reference).
