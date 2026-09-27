<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-summarizers -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# About Configuration Manager Status Summarizers

Summarizers are summary classes that help you determine the health, or status, of different aspects of your Configuration Manager site. The summaries, which are produced from status messages, states, and counts, give you a real-time view of the health of Configuration Manager sites, components, packages, and advertisements.

Status summarizer classes summarize the status message data. Most of the summarizers create two views of the messages: a site view and a site hierarchy view.

All the summaries, except site system, are event-driven summaries. They respond in real time to changes that are taking place in Configuration Manager. Only the site system status summary polls for its information, according to a schedule that you can set.

Note

The `SMS_SummarizerStatus` class can be used to identify the registered summarizers.

## Site and Component Status

These summarizers group summaries of two kinds of data: software component health and physical system health.

You can determine the overall health of your site by using the stoplight status value in the `SMS_SummarizerSiteStatus` class, or you can determine the health of your storage objects by using the `SMS_SiteSystemSummarizer` class. For more information, see [How to Determine the Health of a Configuration ManagerSite](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-determine-the-health-of-a-configuration-manager-site). You can access these and other classes by getting, enumerating, and querying summarizer objects. However, the `SMS_ComponentSummarizer` and `SMS_SiteDetailSummarizer` classes can only be queried — you cannot get or enumerate these objects. Your queries must include a tally interval that defines the period of time from which you want summary information. For example, the following query asks for the count informational, warning, and error messages since Monday.

```
SELECT Infos, Warnings, Errors
FROM SMS_SiteDetailSummarizer
WHERE TallyInterval = "00011280001A2000"
```

Note

You cannot add other conditions like SiteCode to the WHERE clause. Adding other conditions will generate an error.

For information about using this query, see [How to Perform a Synchronous Configuration Manager Query by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code) and [How to Perform a Synchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi).

For more information about using tally intervals, see [About Configuration Manager Tally Intervals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-tally-intervals).

The component summarizers track the progress of advertised programs as they are advertised and run on the client computers.

Site system and package status summaries track the state changes instead of counting the error messages. For example, site system status summaries react to changes in free disk space on a site system. If the free space falls below the threshold you set, the site system's status summary health indicator changes.

The summarizer classes are:

| Summarizer | Description |
| --- | --- |
| [SMS\_ComponentSummarizer Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_componentsummarizer-server-wmi-class) | Represents a component summarizer that reports on the health of individual Configuration Manager components. |
| [SMS\_SiteDetailSummarizer Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_sitedetailsummarizer-server-wmi-class) | Represents a site detail summarizer that reports on the per-site status of components and the system. |
| [SMS\_SiteSystemSummarizer Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_sitesystemsummarizer-server-wmi-class) | Represents a site system summarizer that reports physical system health data for each system and each system role in the Configuration Manager site. |
| [SMS\_SummarizerRootStatus Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_summarizerrootstatus-server-wmi-class) | Represents a summarizer for the overall health of the entire site hierarchy. |
| [SMS\_SummarizerSiteStatus Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_summarizersitestatus-server-wmi-class) | Represents a summarizer for the overall health of each site. |

## Software Distribution Health

You can determine the status of advertisements and packages by using the software distribution summarizers.

### Package Summarizers

Package summarizers are used to track the progress of packages as they are moved to their assigned distribution points. For more information, see [How to Determine Package Status](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-determine-package-status)

Package status summaries track the state changes instead of counting the error messages. For example, The package status summaries track items such as how many clients have installed each package.

The package summarizer classes are:

| Summarizer | Description |
| --- | --- |
| [SMS\_PackageStatusDetailSummarizer Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusdetailsummarizer-server-wmi-class) | Tracks the progress of each package as it places the software source files on its distribution point. The reported package status is for an individual site. |
| [SMS\_PackageStatusDistPointsSummarizer Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusdistpointssummarizer-server-wmi-class) | Tracks the progress of loading the package source files on the distribution point. The reported package status is for an individual site. |
| [SMS\_PackageStatusRootSummarizer Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagestatusrootsummarizer-server-wmi-class) | Tracks the progress of each package as it places the software source files on its distribution point. The reported package status is for all sites in the hierarchy. |

## See Also

[About Configuration Manager Tally Intervals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-tally-intervals) [How to Determine the Health of a Configuration Manager Site](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-determine-the-health-of-a-configuration-manager-site) [How to Read The Tally Intervals For a Configuration Manager Site](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-read-the-tally-intervals-for-a-configuration-manager-site)
