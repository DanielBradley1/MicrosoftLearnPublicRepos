<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/protect/tech-ref/bitlocker/troubleshoot -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Troubleshoot BitLocker

*Applies to: Configuration Manager \(current branch\)*

Use the information in this article to help you troubleshoot issues with BitLocker management in Configuration Manager.

## Server error in self-service

When trying to open the self-service portal \(`https://webserver.contoso.com/SelfService`\) for the first time, you see the following error message:

```error
Configuration Error - Server Error in '/SelfService' Application

Description: An error occurred during the processing of a configuration file required to service this request. Please review the specific error details below and modify your configuration file appropriately.

Parser Error Message: Could not load file or assembly 'System.Web.Mvc, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified.
```

To fix this issue, make sure you installed the [prerequisite](https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/bitlocker-management#prerequisites) for **Microsoft ASP.NET MVC 4.0** on the web server.

## See also

For more information about using BitLocker event logs, see [BitLocker event logs](https://learn.microsoft.com/en-us/intune/configmgr/protect/tech-ref/bitlocker/about-event-logs).

For a list of known errors and possible causes for event log entries, see the following articles:

- [Client event logs](https://learn.microsoft.com/en-us/intune/configmgr/protect/tech-ref/bitlocker/client-event-logs)
- [Server event logs](https://learn.microsoft.com/en-us/intune/configmgr/protect/tech-ref/bitlocker/server-event-logs)

To understand why clients are reporting not compliant with the BitLocker management policy, see [Non-compliance codes](https://learn.microsoft.com/en-us/intune/configmgr/protect/tech-ref/bitlocker/non-compliance-codes).
