<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/updates-faq -->
<!-- Sitemap-Last-Modified: 2026-08-31 -->

# In-console updates FAQ

## Why don't I see certain updates in my console?

If you can't find a specific update in your console after a successful sync with the Microsoft cloud service, this behavior might be because of one of the following reasons:

- The update requires a configuration that your infrastructure doesn't use, or your current product version doesn't fulfill a prerequisite for receiving the update.

  If you think you have the required configurations and prerequisites for a missing update, confirm the service connection point is in online mode. Then, use the **Check for Updates** option in the **Updates and Servicing** node to force a check. If your service connection point is in offline mode, use the service connection tool to manually sync with the cloud service.
- Your account lacks the correct role-based administration permissions to view updates in the Configuration Manager console. For more information, see [Permissions to manage updates](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/prepare-in-console-updates#permissions).

## Why did the current branch name change with version 2103?

To better align with other releases within Microsoft Endpoint Manager, starting in the year 2021 the current branch version names will be 2103, 2107, and 2111. They will still release every four months, and release at the same time of the year.
