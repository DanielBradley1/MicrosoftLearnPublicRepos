<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-remove-personal-data -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Remove personal data for Microsoft Entra application proxy

## Overview

Microsoft Entra application proxy requires that you install connectors on your devices, which means that there might be personal data on your devices. This article provides steps for how to delete that personal data to improve privacy.

## Where is the personal data?

It's possible for application proxy to write personal data to the following log types:

- connector event logs
- Windows event logs

## Remove personal data from Windows event logs

For information on how to configure data retention for the Windows event logs, see the Windows event log settings documentation. For more information about Windows event logs, see [Using Windows Event Log](https://learn.microsoft.com/en-us/windows/win32/wes/using-windows-event-log).

Note

For information about viewing or deleting personal data, please review Microsoft's guidance on the [Windows data subject requests for the GDPR](https://learn.microsoft.com/en-us/microsoft-365/compliance/gdpr-dsr-windows) site. For general information about GDPR, see the [GDPR section of the Microsoft Trust Center](https://www.microsoft.com/trust-center/privacy/gdpr-overview) and the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

## Remove personal data from connector event logs

To ensure the application proxy logs don't have personal data, you can either:

- Delete or view data when needed, or
- Turn off logging

Use the following sections to remove personal data from connector event logs. You must complete the removal process for all devices on which the connector is installed.

Note

This article provides steps about how to delete personal data from the device or service and can be used to support your obligations under the GDPR. For general information about GDPR, see the [GDPR section of the Microsoft Trust Center](https://www.microsoft.com/trust-center/privacy/gdpr-overview) and the [GDPR section of the Service Trust portal](https://servicetrust.microsoft.com/ViewPage/GDPRGetStarted).

### View or export specific data

To view or export specific data, search for related entries in each of the connector event logs. The logs are located at `C:\ProgramData\Microsoft\Microsoft AAD private network connector\Trace`.

Since the logs are text files, you can use [findstr](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/findstr) to search for text entries related to a user.

To find personal data, search log files for UserID.

To find personal data logged by an application that uses Kerberos Constrained Delegation, search for these components of the username type:

- On-premises user principal name
- Username part of user principal name
- Username part of on-premises user principal name
- On-premises security accounts manager \(SAM\) account name

### Delete specific data

To delete specific data:

1. Generate a new log file. Restart the Microsoft Entra private network connector service. The new log file enables you to delete or modify the old log files.
2. Follow the [View or export specific data](#view-or-export-specific-data) process described previously to find information that needs to be deleted. Search all of the connector logs.
3. Either delete the relevant log files or selectively delete the fields that contain personal data. You can also delete all old log files if you don’t need them anymore.

### Turn off connector logs

One option to ensure the connector logs don't contain personal data is to turn off the log generation. To stop generating connector logs, remove the following highlighted line from `C:\Program Files\Microsoft Entra private network connector\MicrosoftEntraPrivateNetworkConnectorService.exe.config`.

![Screenshot that shows a code snippet with the highlighted code to remove.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-remove-personal-data/01.png)

## Next steps

For an overview of application proxy, see [How to provide secure remote access to on-premises applications](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy).
