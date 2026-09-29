<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/investigate-files -->
<!-- Sitemap-Last-Modified: 2025-09-29 -->

# Investigate a file

Investigate the details of a file associated with a specific alert, behavior, or event to help determine if the file exhibits malicious activities, identify the attack motivation, and understand the potential scope of the breach.

There are many ways to access the detailed profile page of a specific file. For example, you can use the search feature, click on a link from the **Alert process tree**, **Incident graph**, **Artifact timeline**, or select an event listed in the **Device timeline**.

Once on the detailed profile page, you can switch between the new and old page layouts by toggling **new File page**. The rest of this article describes the newer page layout.

You can get information from the following sections in the file view:

- File details and PE metadata \(if it exists\)
- Incidents and alerts
- Observed in organization
- File names
- File content and capabilities \(if a file has been analyzed by Microsoft\)

You can also take action on a file from this page.

## File actions

The file actions are above the file information cards at the top of the profile page. Actions you can perform here include:

- Stop and quarantine
- Manage indicator
- Download file
- Ask Defender Experts
- Manual actions
- Go hunt
- Deep analysis

See [take response action on a file](https://learn.microsoft.com/en-us/defender-endpoint/respond-file-alerts) for more information on these actions.

## File page overview

The file page offers an overview of the file's details and attributes, the incidents and alerts where the file is seen, file names used, the number of devices where the file was seen in the last 30 days, including the dates when the file was first and last seen in the organization, Virus Total detection ratio, Microsoft Defender Antivirus detection, the number of cloud apps connected to the file, and the file's prevalence in devices outside of the organization.

Note

Different users may see dissimilar values in the *devices in organization* section of the file prevalence card. This is because the card displays information based on the role-based access control \(RBAC\) scope that a user has. This means if a user has been granted visibility on a specific set of devices, they will only see the file organizational prevalence on those devices.

[![Screenshot of the File page overview](https://learn.microsoft.com/en-us/defender/media/investigate-files/investigatefiles-fileoverview.png)](https://learn.microsoft.com/en-us/defender/media/investigate-files/investigatefiles-fileoverview.png#lightbox)

## Incidents and alerts

The **Incidents and alerts** tab provides a list of incidents that are associated with the file and the alerts the file is linked to. This list covers much of the same information as the incidents queue. You can choose what kind of information is shown by selecting **Customize columns**. You can also filter the list by selecting **Filter**.

![Screenshot showing incidents and alerts.](https://user-images.githubusercontent.com/96785904/200527005-1fd139dc-7483-4e4c-83ad-855cd198f153.png)

## Observed in organization

The **Observed in organization** tab shows you the devices and cloud apps observed with the file. File history related to devices can be shown up to the last six months, whereas cloud apps-related history is up to the last 30 days

### Devices

This section shows all the devices where the file is detected. The section includes a trending report identifying the number of devices where the file has been observed in the past 30 days. Below the trendline, you can find detailed information on the file on each device where it is seen, including file execution status, first and last seen events on each device, initiating process and time, and file names associated with a device.

You can click on a device on the list to explore the full six months file history on each device and pivot to the first seen event in the device timeline.

[![Screenshot of the devices page within a file](https://learn.microsoft.com/en-us/defender/media/investigate-files/investigatefiles-devices.png)](https://learn.microsoft.com/en-us/defender/media/investigate-files/investigatefiles-devices.png#lightbox)

### Cloud apps

Note

The Defender for Cloud Apps workload must be enabled to see file information related to cloud apps.

This section shows all the cloud applications where the file is observed. It also includes information like the file's names, the users associated with the app, the number of matches to a specific cloud app policy, associated apps' names, when the file was last modified, and the file's path.

[![Screenshot of the cloud apps page within a file](https://learn.microsoft.com/en-us/defender/media/investigate-files/investigatefiles-cloudapps.png)](https://learn.microsoft.com/en-us/defender/media/investigate-files/investigatefiles-cloudapps.png#lightbox)

## File names

The **File names** tab lists all names the file has been observed to use, within your organizations.

[![The File names tab](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-file-names.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-file-names.png#lightbox)

## File content and capabilities

Note

The file content and capabilities views depend on whether Microsoft analyzed the file.

The File content tab lists information about portable executable \(PE\) files, including process writes, process creation, network activities, file writes, file deletes, registry reads, registry writes, strings, imports, and exports. This tab also lists all the file's capabilities.

[![Screenshot of a file's content](https://learn.microsoft.com/en-us/defender/media/investigate-files/investigatefiles-filecontent.png)](https://learn.microsoft.com/en-us/defender/media/investigate-files/investigatefiles-filecontent.png#lightbox)

The file capabilities view lists a file's activities as mapped to the MITRE ATT&CK™ techniques.

[![Screenshot of a file's capabilities](https://learn.microsoft.com/en-us/defender/media/investigate-files/investigatefiles-filecapabilities.png)](https://learn.microsoft.com/en-us/defender/media/investigate-files/investigatefiles-filecapabilities.png#lightbox)

## Related topics

- [View and organize the Microsoft Defender for Endpoint queue](https://learn.microsoft.com/en-us/defender-endpoint/alerts-queue)
- [Manage Microsoft Defender for Endpoint alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts?toc=/defender-endpoint/toc.json&bc=/defender-endpoint/breadcrumb/toc.json#manage-alerts)
- [Investigate Microsoft Defender for Endpoint alerts](https://learn.microsoft.com/en-us/defender-endpoint/investigate-alerts)
- [Investigate devices in the Microsoft Defender for Endpoint Devices list](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines)
- [Investigate an IP address associated with a Microsoft Defender for Endpoint alert](https://learn.microsoft.com/en-us/defender-endpoint/investigate-ip)
- [Investigate a domain associated with a Microsoft Defender for Endpoint alert](https://learn.microsoft.com/en-us/defender-endpoint/investigate-domain)
- [Investigate a user account in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/investigate-user)
- [Take response actions on a file](https://learn.microsoft.com/en-us/defender-endpoint/respond-file-alerts)
