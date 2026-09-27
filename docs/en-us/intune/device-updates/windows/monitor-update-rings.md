<!-- Source: https://learn.microsoft.com/en-us/intune/device-updates/windows/monitor-update-rings -->
<!-- Sitemap-Last-Modified: 2026-04-09 -->

# Reports for Windows update ring policies

Intune offers integrated report views for the Windows update ring policies you deploy. These views display details about the update ring deployment and status.

To access update ring policies reports:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** > **Windows**
2. Under **Manage updates**, select **Windows updates**
3. Select the **Update rings** tab
4. Select an update ring policy:

   [![Screen capture of the default view for update ring policy.](https://learn.microsoft.com/en-us/intune/device-updates/windows/media/shared/update-rings.png)](https://learn.microsoft.com/en-us/intune/device-updates/windows/media/shared/update-rings.png#lightbox)

On the policy page view:

- **Device and user check-in status**: The default report view for this policy. This default view includes a high-level bar chart that displays a count of devices reporting four status values for this policy, and a color bar that visually represents the percentage of devices reporting each status by color. This view displays the following four status results for the policy:

  - Succeeded
  - Error
  - Conflict
  - Not applicable

- **View report**: This button opens a more detailed report view for *Device and user check-in status*. The detailed report view includes a chart and color bar similar to that from the preceding high-level view, but reports one the additional status of **In progress**.

  This view also includes device specific details that include:

  - Device name
  - Logged in user
  - Check-in status
  - Last report modification time


  ![Screen capture that shows details available from the View report action.](https://learn.microsoft.com/en-us/intune/device-updates/windows/media/monitor-update-rings/report-view-details.png)


  From this report view, you can select a device to drill in to view the list of the settings in the policy, and the status of the selected device for each of those settings. Additional drill-in is available by selecting a setting to open the *Setting details*. The *Setting details* display the name of the setting, the devices status \(State\) for that setting, and a list of profiles that manage the setting and that are assigned to the device. This is useful to help identify the source of a settings conflict.

- **Two additional report tiles**: You can select the tiles for the following reports to view additional details:

  - **Device assignment status**: This report shows all the devices that are targeted by the policy, including devices in a pending policy assignment state.

    For this report, you can select one or more status details you are interested in, and then select *Generate report* to update the view with only that information. In this following image, we have generated a report that displays only the devices that were successfully assigned this policy:

    ![Image of the results of the Assignment status report.](https://learn.microsoft.com/en-us/intune/device-updates/windows/media/monitor-update-rings/successful-assignment-view.png)

    This report supports drilling in to view the list of settings, with subsequent drill-in as seen in for the full report view available from the *View report* button.
  - **Per setting status**: View the configuration status of each setting for this policy across all devices and users. This view present a simple view of each setting in the policy, and the count of assigned devices that have success, error, or conflict. This report view doesn't support drilling in for additional detail.

## Windows Update for Business reports

You can also monitor Windows update rollouts by using Windows Update for Business reports. Windows Update for Business reports is a cloud-based solution that provides information about your Microsoft Entra joined devices' compliance with Windows updates. It's offered through the Azure portal, and it's included as part of the Windows licenses.

To use this solution, you can use Intune to configure the required settings on your Windows devices.

For more information, see [Windows Update for Business reports overview](https://learn.microsoft.com/en-us/windows/deployment/update/wufb-reports-overview).
