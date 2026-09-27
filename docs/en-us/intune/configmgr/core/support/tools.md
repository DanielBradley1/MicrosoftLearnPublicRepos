<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/support/tools -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# Configuration Manager Tools

*Applies to: Configuration Manager \(current branch\)*

The Configuration Manager tools primarily include [client-based](#client-tools) and [server-based tools](#server-tools). Use these tools to help support and troubleshoot your Configuration Manager infrastructure.

These tools are included in the `CD.Latest\SMSSETUP\Tools` folder on the site server. No further installation is required. Use these versions of the tools with supported versions of Configuration Manager current branch.

All Windows operating systems listed as supported clients in [Supported operating systems for clients and devices](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices) are supported for use with these tools.

Note

For supported versions of Configuration Manager current branch, use the versions of the tools in the CD.Latest folder on the site server. Some tools were formerly in the toolkit but not included current branch. These legacy tools are no longer supported.

## Client tools

These tools are in the `ClientTools` subfolder:

- [Client Spy](https://learn.microsoft.com/en-us/intune/configmgr/core/support/clispy): Troubleshoot issues related to software distribution, inventory, and metering
- [Deployment Monitoring Tool](https://learn.microsoft.com/en-us/intune/configmgr/core/support/deployment-monitoring-tool): Troubleshoot applications, updates, and baseline deployments
- [Policy Spy](https://learn.microsoft.com/en-us/intune/configmgr/core/support/policy-spy): View policy assignments
- [Power Viewer Tool](https://learn.microsoft.com/en-us/intune/configmgr/core/support/power-viewer-tool): View status of power management feature
- [Send Schedule Tool](https://learn.microsoft.com/en-us/intune/configmgr/core/support/send-schedule-tool): Trigger schedules and evaluations of configuration baselines

Note

The `ClientTools` folder also includes the file Microsoft.Diagnostics.Tracing.EventSource.dll. Several client tools require this library. You can't directly use it.

## Server tools

These tools are in the `ServerTools` subfolder:

- [DP Job Queue Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/support/dp-job-manager): Troubleshoots content distribution jobs to distribution points
- [Collection Evaluation Viewer](https://learn.microsoft.com/en-us/intune/configmgr/core/support/ceviewer): View collection evaluation details

  Important

  Starting in Configuration Manager version 2103, this standalone tool isn't supported. The tool is no longer included with the Configuration Manager installation source. Starting in version 2010, its functionality is built-in to the console. For more information, see, [How to view collection evaluation](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/collection-evaluation-view).
- [Content Library Explorer](https://learn.microsoft.com/en-us/intune/configmgr/core/support/content-library-explorer): View contents of the content library single instance store
- [Content Library Transfer](https://learn.microsoft.com/en-us/intune/configmgr/core/support/content-library-transfer): Transfers content library between drives
- [Content Ownership Tool](https://learn.microsoft.com/en-us/intune/configmgr/core/support/content-ownership-tool): Changes ownership of orphaned packages. These packages exist in the site without an owning site server.
- [Role-based Administration and Auditing Tool](https://learn.microsoft.com/en-us/intune/configmgr/core/support/rbaviewer): Helps administrators audit roles configuration

  Note

  Starting in version 2107, RBAViewer has moved from `<installdir>\tools\servertools\rbaviewer.exe`. It's now located in the Configuration Manager console directory. After you install the console, RBAViewer.exe will be in the same directory. The default location is `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\bin\rbaviewer.exe`.
- [Run Meter Summarization Tool](https://learn.microsoft.com/en-us/intune/configmgr/core/support/run-meter-summ): Run metering summarization task and analyze metering data

Note

The ServerTools folder also includes the following files:

- AdminUI.WqlQueryEngine.dll
- Microsoft.ConfigurationManagement.ManagementProvider.dll
- Microsoft.Diagnostics.Tracing.EventSource.dll

Several server tools require these libraries. You can't directly use them.

## More tools in the folder

The following tools are in the `CD.Latest\SMSSETUP\TOOLS` folder on the site server:

- [CMTrace](https://learn.microsoft.com/en-us/intune/configmgr/core/support/cmtrace): View, monitor, and analyze Configuration Manager log files.
- [CMPivot](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/cmpivot): Use the standalone version of this tool to query real-time data from clients.
- [Update reset tool](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/update-reset-tool): Fix issues when in-console updates have problems downloading or replicating.
- [Configuration Manager group policy administrative template](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-to-windows-computers#configure-and-assign-client-installation-properties-by-using-a-group-policy-object): Configure and assign client installation properties by using a group policy object.
- [Content library cleanup tool](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/content-library-cleanup-tool): Remove orphaned content from a distribution point.
- [Extend and migrate on-premises site to Microsoft Azure](https://learn.microsoft.com/en-us/intune/configmgr/core/support/azure-migration-tool): Helps you to programmatically create Azure virtual machines \(VMs\) for Configuration Manager.
- [Synchronize Microsoft 365 Apps updates from a disconnected software update point](https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/synchronize-office-updates-disconnected) \(OfflineUpdateExporter\): Import Microsoft 365 Apps updates from an internet connected WSUS server into a disconnected Configuration Manager environment.
- [Configure client communication ports](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/configure-client-communication-ports): Reconfigure the port numbers for existing clients.
- [Service Connection Tool](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/hierarchy-maintenance-tool-preinst.exe): Keep your site up to date when your service connection point is offline.
- [Support Center](https://learn.microsoft.com/en-us/intune/configmgr/core/support/support-center): Gather information from clients for easier analysis when troubleshooting.

  **OneTrace** is a modern log viewer with Support Center. It works similarly to CMTrace, with improvements. For more information, see [Support Center OneTrace](https://learn.microsoft.com/en-us/intune/configmgr/core/support/support-center-onetrace).
- [Send feedback that you saved for later submission](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/product-feedback#send-feedback-that-you-saved-for-later-submission) \(UploadOfflineFeedback\): Save your product feedback locally and submit it later.

## Other tools

- [Hierarchy Maintenance Tool](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/hierarchy-maintenance-tool-preinst.exe): Use **Preinst.exe** in the `\<SiteServerName>\SMS_<SiteCode>\bin\X64\00000409` shared folder on the site server to pass commands to the hierarchy manager component.
- [Microsoft Deployment Toolkit \(MDT\)](https://learn.microsoft.com/en-us/intune/configmgr/mdt/use-the-mdt): A collection of tools, processes, and guidance for automating desktop and server OS deployments.
- [System Center Updates Publisher \(SCUP\)](https://learn.microsoft.com/en-us/intune/configmgr/sum/tools/updates-publisher): A stand-alone tool to manage and import custom software updates.
- [Package Conversion Manager](https://learn.microsoft.com/en-us/intune/configmgr/apps/pcm/package-conversion-manager): Convert legacy packages into applications.
