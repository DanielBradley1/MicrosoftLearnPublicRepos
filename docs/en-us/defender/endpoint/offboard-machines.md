<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/offboard-machines -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# Offboard devices from Microsoft Defender for Endpoint

When you offboard a device from Defender for Endpoint, no new detections, vulnerability, or security data are sent to the Microsoft Defender portal. Seven days after offboarding a device, its status changes to [inactive](https://learn.microsoft.com/en-us/defender-endpoint/fix-unhealthy-sensors#inactive-devices). Devices that weren't active within the past 30 days are not factored into your organization's [exposure score](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-exposure-score).

Past data, such as alerts, vulnerabilities, and the device timeline, for an offboarded device is displayed in the Microsoft Defender portal until the [configured retention period](https://learn.microsoft.com/en-us/defender-endpoint/data-storage-privacy#data-retention) expires. You also see the device profile \(without data\) in the device inventory for up to 180 days. To view data for active devices only, you can use filters, such as [sensor health state](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview#apply-filters), [device tags](https://learn.microsoft.com/en-us/defender-endpoint/machine-tags), or [device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

## Prerequisites

Offboarding is supported on devices running the following operating systems:

- Windows client operating systems
- Windows Server 2012 R2 and later
- Linux \(client and server\)
- macOS
- Android and iOS
- Azure Stack HCI OS, version 23H2 and later

## Offboard client devices

### Offboard Windows client devices

Navigate to [Microsoft Defender portal](https://security.microsoft.com), in the navigation pane, select **Settings** > **Offboard**, and then select an operating system to start the offboarding process.

You can also use other methods, such as:

- [Offboard devices using a local script](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script#offboard-devices-using-a-local-script)
- [Offboard devices using Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-gp#offboard-devices-using-group-policy)
- [Offboard devices using Mobile Device Management tools](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-mdm#offboard-devices-using-mobile-device-management-tools)
- [Offboard devices using the API](https://learn.microsoft.com/en-us/defender-endpoint/api/offboard-machine-api)

### Offboard Linux client devices

For information about offboarding and uninstalling Microsoft Defender for Endpoint on Linux clients, see [Offboard Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-off-board-endpoints).

### Offboard MacOS devices

In the following procedure, steps 1 and 2 are optional if you do not want to see these devices as retired in the "Device inventory" for 180 days.

1. Create a [device tag](https://learn.microsoft.com/en-us/defender-endpoint/machine-tags), and name the tag `decommissioned`. Assign the tag to the Mac devices that you want to offboard from Defender for Endpoint.
2. Create a [Device group](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups) and name it something like, `Decommissioned Mac`. Assign this tag to an appropriate user group.
3. Remove policies for [Tamper Protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-macos-configure). See [Set preferences on Mac: Tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences#tamper-protection), or turn off tamper protection by using [local configuration](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-macos-configure#configure-tamper-protection-locally).
4. In the [Microsoft Defender portal](https://security.microsoft.com), navigate to, **System** > **Settings** > **Endpoints** > **Device management** > **Offboarding**. Select **macOS** in Step 1, then choose your preferred deployment method, and select **Download package** to download the offboarding package.

   Or, if you're using a non-Microsoft device management solution, disable integration with Defender for Endpoint.
5. Uninstall the Defender for Endpoint app on Mac devices.
6. Remove Mac devices from the group for system extension policies if an MDM was used to set them.

### Offboard Android or iOS devices

To offboard an Android or iOS device, uninstall the Microsoft Defender app on the device.

## Offboard cloud and on-premises servers

Offboard an Azure environment in one step by turning off Defender for Servers for the subscription. Eligible servers are offboarded automatically, without running an offboarding package on each server. To offboard only selected servers, use manual offboarding.

### Choose an offboarding path

Choose a path based on whether you want to offboard servers across an Azure subscription or only selected servers.

| Outcome | What to do |
| --- | --- |
| Offboard an Azure subscription and all servers in it | Turn off Defender for Servers for the subscription. Follow [automatic Azure offboarding](#offboard-servers-in-an-azure-subscription). |
| Offboard individual servers | Follow [manual endpoint offboarding](#offboard-individual-servers) using a supported method for the operating system. |

Note

- **Change active Defender for Servers plan:** Follow the [plan-change procedure](https://learn.microsoft.com/en-us/azure/defender-for-cloud/tutorial-enable-servers-plan#disable-defender-for-servers-on-a-subscription). Review the subscription and resource settings before making changes.
- **Uninstall Microsoft Defender for Endpoint:** Follow the uninstall instructions for the server's operating system. Offboarding doesn't uninstall the software.

### Prepare for server offboarding

1. Record affected servers, existing coverage, and deployment policies.
2. Review open investigations, evidence-retention needs, and any plans to onboard the server again or reinstall endpoint software.
3. Remove conflicting onboarding assignments so deployment tools don't reverse the change.
4. For Direct onboarding, review [who is affected](https://learn.microsoft.com/en-us/azure/defender-for-cloud/onboard-machines-with-defender-for-endpoint#who-is-affected) before changing a shared setting.

### Offboard servers in an Azure subscription

To offboard an Azure environment, turn off Defender for Servers for its subscription in the Azure portal. This automatically offboards eligible servers from Defender for Endpoint. No need to run an offboarding package on each server.

- Use the subscription's Defender for Servers plan setting, not deletion of the Azure environment connector.
- Changing from Plan 2 to Plan 1 or moving a server between subscriptions doesn't trigger automatic offboarding.

To start offboarding and verify the result:

1. In **Microsoft Defender for Cloud** in the Azure portal, identify the subscription where you want to turn off Defender for Servers.
2. Turn off the plan using the [plan-change procedure](https://learn.microsoft.com/en-us/azure/defender-for-cloud/tutorial-enable-servers-plan#disable-defender-for-servers-on-a-subscription). This is the only action required to initiate offboarding. The software automatically handles intent validation, MDE extension removal, and endpoint offboarding.
3. Allow processing to complete, and then [verify each outcome](#validate-server-offboarding). Offboarding can take up to one hour for large subscriptions. If machines are powered off, the software retries later.

Use the subscription's plan control to initiate offboarding, not deletion of the Azure environment connection.

Automatic offboarding disconnects the endpoint from its current Defender for Endpoint organization and stops EDR reporting to that organization. It doesn't uninstall the endpoint software or remove historical device records. Software or record presence alone doesn't indicate a failure, and the plan setting alone doesn't confirm that offboarding is complete. Manual endpoint offboarding or uninstall isn't required as part of the automatic flow.

Note

If you turn the plan back on before offboarding completes, the offboarding and onboarding actions run asynchronously. Defender for Endpoint is onboarded again after a few hours. Turning the plan back on doesn't immediately cancel offboarding.

### Offboard individual servers

Use manual offboarding to stop selected servers from reporting to Defender for Endpoint. Follow the method below for your operating system and management tool.

**Download an offboarding package \(if required\)**

Navigate to [Microsoft Defender portal](https://security.microsoft.com), in the navigation pane, select **Settings** > **Cloud Security** > **Server security - Onboard and Manage** > **Manage offboarding**, and then select an operating system to start the offboarding process.

Note

Use an account authorized to download the package, and then follow the relevant method's operating-system and package instructions.

Download a current package for the correct tenant, check its expiration, and store it securely. Package formats and validity periods differ by method.

For local-script or Configuration Manager offboarding, select the Windows version group specified in that method's instructions. The generic **Windows** option opens the separate Defender deployment tool workflow, not the version-specific package workflow.

Choose a method for your operating system and management tool. Download an offboarding package only if the selected procedure requires one.

| Method | Procedure |
| --- | --- |
| Linux script, JSON file, API, or uninstall | [Offboard or uninstall on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-off-board-endpoints) |
| Windows Configuration Manager | [Offboard with Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-sccm#offboard-devices-using-configuration-manager) |
| Windows local script | [Offboard with a local script](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script#offboard-devices-using-a-local-script) |
| Windows Group Policy | [Group Policy offboarding](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-gp#offboard-devices-using-group-policy) |
| Mobile device management | [Mobile Device Management offboarding](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-mdm#offboard-devices-using-mobile-device-management-tools) |
| API automation | [Offboard machine API](https://learn.microsoft.com/en-us/defender-endpoint/api/offboard-machine-api) |

### Validate server offboarding

| Intended change | Check |
| --- | --- |
| Plan coverage | Confirm the intended plan state in Defender for Cloud. |
| Endpoint offboarding | Confirm the local offboarding state using the method-specific procedure, and then check that new endpoint data stops. Inactivity alone isn't proof of offboarding. |
| Software removal | Confirm the relevant application, package, or service is absent using operating-system tools. |
| No automatic return | Recheck after the deployment system's policy refresh. |

### Historical records and retention

Past endpoint data can remain visible under the configured retention policy. A retained device record doesn't prove that protection or reporting is still active. See [data retention](https://learn.microsoft.com/en-us/defender-endpoint/data-storage-privacy#data-retention).

## Related content

- [Offboard or uninstall Microsoft Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/linux-off-board-endpoints)
