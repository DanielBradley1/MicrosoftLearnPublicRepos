<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/timeline -->
<!-- Sitemap-Last-Modified: 2023-02-22 -->

# Tenant attach: Device timeline in the admin center

*Applies to: Configuration Manager \(current branch\)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**. When Configuration Manager synchronizes a device to Microsoft Intune through tenant attach, you can see a timeline of events. This timeline shows past activity on the device that can help you troubleshoot problems.

## Prerequisites

The following items are needed to use the timeline from the admin center:

- All of the prerequisites for [Tenant attach: ConfigMgr client details](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/client-details#prerequisites).
- Enable Endpoint analytics data collection in Configuration Manager:

  1. In the Configuration Manager console, go to **Administration** > **Client Settings** > **Default Client Settings**.
  2. Right-click and select **Properties** then select the **Computer Agent** settings.
  3. Set **Enable Endpoint analytics data collection** to **Yes**.

     - Only events collected after the client receives this policy will be visible in the admin center. Events prior to receiving the policy won't be accessible.

## Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection** in Configuration Manager.
- The **Read Resource** permission under **Collection** in Configuration Manager.
- The **Notify Resource** permission under **Collection** in Configuration Manager.
- An [Intune role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview) assigned to the user

## Generate events

Devices send events once a day to the admin center. Only events collected after the client receives the **Enable Endpoint analytics data collection** policy are visible in the admin center. Generate test events easily by installing an application or an update from Configuration Manager, or restart the device. Events are kept for 30 days. Use the [chart](#collected-events) to view events that are collected.

## Collected events

| Event name | Provider name | Event ID |
| --- | --- | --- |
| Application Error | Application Error | 1000 |
| Application Hang | Application Hang | 1002 |
| Kernel Crash | Microsoft-Windows-WER-SystemErrorReporting | 1001 |
| Application Crash | Windows Error Reporting | 1001 |
| Windows Update Agent – Update Installation | Microsoft-Windows-WindowsUpdateClient | 19 |
| Unknown Shutdown | Boot | 0 |
| Initiated Shutdown | Boot | 1074 |
| Abnormal Shutdown | Boot | 41 |
| Boundary Group Change | Microsoft-ConfigMgr | 20000 |
| Application Deployment | Microsoft-ConfigMgr | 20001 |
| Configuration Manager – Update Installation | Microsoft-ConfigMgr | 20002 |
| Firmware version change | Microsoft-ConfigMgr | 20003 |
| Configuration Manager Reboot request | Microsoft-ConfigMgr | 20005 |
| Client repair | Microsoft-ConfigMgr | 20006 |
| State resync | Microsoft-ConfigMgr | 20007 |
| Inventory resync | Microsoft-ConfigMgr | 20008 |

## View the timeline

1. In a browser, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions).
4. Select **Timeline**. By default, you're shown events from the last 24 hours.

   - Use the **Filter** button to change the **Time range**, **Event levels**, and **Provider name**.
   - If you select on an event, you'll see the detailed message for it.
   - Select **Sync** to fetch the recent data generated on client. The device sends events once a day to the admin center by default.
   - Select **Refresh** to reload the page and to see newly collected events.


   [![Timeline of events for a device](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/7141381-timeline.png)](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/media/7141381-timeline.png#lightbox)

## Known issues

You will receive a time out error if the following condition applies:

- You're opening **Timeline** for the very first time after restarting SMSExecutive on the service connection point's on-premises server.

To work around the issue, reload the **Timeline** page.

## Next steps

[Troubleshoot the device timeline](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/troubleshoot-timeline)
