<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/offboard-machines -->
<!-- Sitemap-Last-Modified: 2026-09-08 -->

# Offboard devices

When you offboard a device from Defender for Endpoint, no new detections, vulnerability, or security data are sent to the Microsoft Defender portal. Seven days after offboarding a device, its status changes to [inactive](https://learn.microsoft.com/en-us/defender-endpoint/fix-unhealthy-sensors#inactive-devices). Devices that weren't active within the past 30 days are not factored into your organization's [exposure score](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-exposure-score).

Past data, such as alerts, vulnerabilities, and the device timeline, for an offboarded device is displayed in the Microsoft Defender portal until the [configured retention period](https://learn.microsoft.com/en-us/defender-endpoint/data-storage-privacy#data-retention) expires. You also see the device profile \(without data\) in the device inventory for up to 180 days. To view data for active devices only, you can use filters, such as [sensor health state](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview#apply-filters), [device tags](https://learn.microsoft.com/en-us/defender-endpoint/machine-tags), or [device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

## Prerequisites

### Supported operating systems

- Windows client devices
- Windows Server 2012 R2 and later
- Azure Stack HCI OS, version 23H2 and later
- Mac devices
- Linux devices

For information about offboarding and uninstalling Microsoft Defender for Endpoint on Linux, see [Offboard Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-off-board-endpoints).

In the [Microsoft Defender portal](https://security.microsoft.com), in the navigation pane, select **Settings** > **Offboard**, and then select an operating system to start the offboarding process.

You can also use other methods, such as:

- [Offboard devices using a local script](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script#offboard-devices-using-a-local-script)
- [Offboard devices using Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-gp#offboard-devices-using-group-policy)
- [Offboard devices using Mobile Device Management tools](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-mdm#offboard-devices-using-mobile-device-management-tools)
- [Offboard devices using the API](https://learn.microsoft.com/en-us/defender-endpoint/api/offboard-machine-api)

## Offboard servers

In the [Microsoft Defender portal](https://security.microsoft.com), in the navigation pane, select **Settings** > **Offboard**, and then select an operating system to start the offboarding process.

You can also use other methods, such as:

- [Offboard devices using Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-gp#offboard-devices-using-group-policy)
- [Offboard devices using Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-sccm#offboard-devices-using-configuration-manager)
- [Offboard devices using Mobile Device Management tools](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-mdm#offboard-devices-using-mobile-device-management-tools)
- [Offboard devices using a local script](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script#offboard-devices-using-a-local-script)
- [Offboard devices using the API](https://learn.microsoft.com/en-us/defender-endpoint/api/offboard-machine-api)

### Automatic Azure offboarding

Turning off Defender for Servers for a subscription in the Azure portal automatically offboards eligible servers from Microsoft Defender for Endpoint. Changing from Plan 2 to Plan 1 or moving a machine between subscriptions doesn't trigger automatic offboarding.

To start offboarding and verify the result:

1. In **Microsoft Defender for Cloud** in the Azure portal, identify the subscription where you want to turn off Defender for Servers.
2. Turn off the plan using the [plan-change procedure](https://learn.microsoft.com/en-us/azure/defender-for-cloud/tutorial-enable-servers-plan#disable-defender-for-servers-on-a-subscription). This is the only action required to initiate offboarding. The software automatically handles intent validation, MDE extension removal, and endpoint offboarding.
3. Allow processing to complete, and then verify the result. Offboarding can take up to one hour for large subscriptions. If machines are powered off, the software retries later.

Use the subscription's plan control to initiate offboarding, not deletion of the Azure environment connection.

Automatic offboarding disconnects the endpoint from its current Defender for Endpoint organization and stops EDR reporting to that organization. It doesn't uninstall the endpoint software or remove historical device records. Software or record presence alone doesn't indicate a failure, and the plan setting alone doesn't confirm that offboarding is complete. Manual endpoint offboarding or uninstall isn't required as part of the automatic flow.

Note

If you turn the plan back on before offboarding completes, the offboarding and onboarding actions run asynchronously. Defender for Endpoint is onboarded again after a few hours. Turning the plan back on doesn't immediately cancel offboarding.

## Offboard Mac devices

In the following procedure, steps 1 and 2 are optional if you do not want to see these devices that are retired in the "Device inventory" for 180 days.

1. Create a [device tag](https://learn.microsoft.com/en-us/defender-endpoint/machine-tags), and name the tag `decommissioned`. Assign the tag to the Mac devices that you want to offboard from Defender for Endpoint.
2. Create a [Device group](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups) and name it something like, `Decommissioned Mac`. Assign this tag to an appropriate user group.
3. Remove policies for [Tamper Protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-macos-configure). See [Set preferences on Mac: Tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences#tamper-protection), or turn off tamper protection by using [local configuration](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-macos-configure#configure-tamper-protection-locally).
4. In the [Microsoft Defender portal](https://security.microsoft.com), navigate to, **System** > **Settings** > **Endpoints** > **Device management** > **Offboarding**. Select **macOS** in Step 1, then choose your preferred deployment method, and select **Download package** to download the offboarding package.

   Or, if you're using a non-Microsoft device management solution, disable integration with Defender for Endpoint.
5. Uninstall the Defender for Endpoint app on Mac devices.
6. Remove Mac devices from the group for system extension policies if an MDM was used to set them.

## Offboard Android or iOS devices

To offboard an Android or iOS device, uninstall the Microsoft Defender app on the device.

## Related content

- [Offboard or uninstall Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-off-board-endpoints)
