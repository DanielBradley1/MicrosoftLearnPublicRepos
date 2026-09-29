<!-- Source: https://learn.microsoft.com/en-us/defender-for-iot/manage-devices-inventory -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Discover and manage devices

Microsoft Defender for IoT in the Microsoft Defender portal includes the device inventory, which helps you identify details about specific OT devices. Gathering details about your devices helps your teams proactively investigate vulnerabilities that can compromise your most critical assets. This article describes how to discover and manage your devices in the device inventory. You can filter data in the inventory, explore the inventory, investigate device details, and more. Before you start, review the [prerequisites](#prerequisites).

Learn more about the benefits of OT [device discovery](https://learn.microsoft.com/en-us/defender-for-iot/device-discovery).

Important

This article discusses Microsoft Defender for IoT in the Defender portal \(Preview\).

Some features are not yet available in the Defender portal. If you're interested in these features, or you're an existing customer working on the Azure portal, see the [Defender for IoT on Azure documentation](https://learn.microsoft.com/en-us/azure/defender-for-iot/organizations/overview).

Learn more about the [Defender for IoT management portals](https://learn.microsoft.com/en-us/defender-for-iot/microsoft-defender-iot#what-are-the-different-management-portals-for-microsoft-defender-for-iot).

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Access the Device inventory page

Access the **Device inventory** page by selecting **Devices** from the **Assets** navigation menu in the [Microsoft Defender portal](https://security.microsoft.com/machines).

## Prerequisites

Review the [Defender for IoT prerequisites](https://learn.microsoft.com/en-us/defender-for-iot/prerequisites).

Note

If you don't yet have a Defender for IoT license, the **Device inventory** page lists OT devices without security data. For example, the device name, IP, and category are visible, while the risk level isn't visible. The device inventory also displays a note at the top of the page that indicates the number of unprotected OT devices.

In this case, [onboard Defender for IoT](https://learn.microsoft.com/en-us/defender-for-iot/get-started) to get security value for your OT devices.

## View OT devices

View OT devices as part of the [device inventory](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview#device-inventory-overview).

To customize the device inventory views:

- [Use filters](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview#sort-and-filter-the-device-list)
- [Use columns](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview#use-columns-to-customize-the-device-inventory-views)

Note

Currently, devices discovered in the Defender portal aren't synchronized with the Azure portal, and therefore the list of devices discovered could be different in each portal.

### OT network tag

When a Defender for Endpoint agent is associated with a site, all devices discovered by that agent automatically receive the **Network type: OT** tag in the **Tags** column to show that these devices are part of the site. This tag helps users focus on devices that belong to their OT network.

## Manage OT devices

Use the following options to manage OT devices from the device inventory:

- [Explore the device inventory](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview#explore-the-device-inventory) including search, export to CSV, and more.
- [Onboard devices](https://learn.microsoft.com/en-us/defender-endpoint/onboarding#onboard-devices-using-any-of-the-supported-management-tools).
- [Offboard devices](https://learn.microsoft.com/en-us/defender-endpoint/offboard-machines).
- [Investigate the device details](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines) to identify behaviors or events that might be related to a specific alert.
- In the device details pane, select the ellipsis on the top right to [take response actions on a device](https://learn.microsoft.com/en-us/defender-endpoint/respond-machine-alerts).
- [Manually update the site associated with a device](https://learn.microsoft.com/en-us/defender-for-iot/manage-sites#manually-update-device-site-association) to maintain accurate monitoring of the network traffic.

## Next steps

After you set up and manage your device inventory, prioritize and address security gaps:

- [Prioritize and remediate vulnerabilities](https://learn.microsoft.com/en-us/defender-for-iot/prioritize-vulnerabilities)
