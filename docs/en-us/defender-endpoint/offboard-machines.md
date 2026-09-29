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
