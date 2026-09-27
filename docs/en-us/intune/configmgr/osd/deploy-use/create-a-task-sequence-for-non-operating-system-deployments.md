<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-task-sequence-for-non-operating-system-deployments -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Create a task sequence for non-OS deployments

*Applies to: Configuration Manager \(current branch\)*

Task sequences in Configuration Manager are used to automate different kinds of tasks within your environment. These tasks are primarily designed and tested for deploying operating systems. Configuration Manager has many other features that should be the primary technology that you use for the following scenarios:

- [Application installation](https://learn.microsoft.com/en-us/previous-versions/troubleshoot/configmgr/introduction-to-application-management)

  Note

  Starting in version 2002, install complex applications using task sequences via the application model. Add a deployment type to an app that's a task sequence, either to install or uninstall the app. For more information, see [Create Windows applications](https://learn.microsoft.com/en-us/intune/configmgr/apps/get-started/creating-windows-applications#bkmk_tsdt).

  Starting in version 2010, use the task sequence deployment type of an application to deploy a task sequence to a user-based collection.
- [Software updates installation](https://learn.microsoft.com/en-us/intune/configmgr/sum/understand/software-updates-introduction)
- [Setting configuration](https://learn.microsoft.com/en-us/intune/configmgr/compliance/understand/ensure-device-compliance)

Also consider other Microsoft System Center automation technologies, such as [Orchestrator](https://learn.microsoft.com/en-us/system-center/orchestrator/) and [Service Management Automation](https://learn.microsoft.com/en-us/system-center/sma/).

The power of task sequences lies in their flexibility and how you use them. They can configure client settings, distribute software, update drivers, edit user states, and do other tasks independent of OS deployment. You can create a custom task sequence to add any number of tasks. The use of custom task sequences for non-OS deployment is supported in Configuration Manager. However, if a task sequence results in unwanted or inconsistent results, look at ways to simplify the operation:

- Use simpler steps
- Divide the actions across multiple task sequences
- Take a phased approach to creating and testing the task sequence

## Supported steps

The following steps are supported for use in a non-OS deployment custom task sequence:

- [Check Readiness](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_CheckReadiness)
- [Connect To Network Folder](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_ConnectToNetworkFolder)
- [Download Package Content](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_DownloadPackageContent)
- [Install Application](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_InstallApplication)
- [Install Package](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_InstallPackage)
- [Install Software Updates](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_InstallSoftwareUpdates)
- [Restart Computer](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_RestartComputer)
- [Run Command Line](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_RunCommandLine)
- [Run PowerShell Script](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_RunPowerShellScript)
- [Run Task Sequence](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#child-task-sequence)
- [Set Dynamic Variables](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_SetDynamicVariables)
- [Set Task Sequence Variable](https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable)

## Next steps

[Create a custom task sequence](https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/create-a-custom-task-sequence)
