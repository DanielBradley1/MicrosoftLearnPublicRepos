<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/check-sensor-status -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Check service health at Microsoft Defender for Endpoint

The **Device health** tile provides information on the individual device's ability to provide sensor data and communicate with the Defender for Endpoint service. It reports how many devices require attention and helps you identify problematic devices and take action to correct known issues.

There are two status indicators on the tile that provide information on the number of devices that aren't reporting properly to the service:

- **Misconfigured** - These devices might partially be reporting sensor data to the Defender for Endpoint service and might have configuration errors that need to be corrected.
- **Inactive** - Devices that have stopped reporting to the Defender for Endpoint service for more than seven days in the past month.

Clicking any of the groups directs you to **Device inventory**, filtered according to your choice.

On **Device inventory**, you can filter the health state list by the following status:

- **Active** - Devices that are actively reporting to the Defender for Endpoint service.
- **Misconfigured** - These devices might partially be reporting sensor data to the Defender for Endpoint service but have configuration errors that need to be corrected. Misconfigured devices can have either one or a combination of the following issues:

  - **No sensor data** - Devices has stopped sending sensor data. Limited alerts can be triggered from the device.
  - **Impaired communications** - Ability to communicate with device is impaired. Sending files for deep analysis, blocking files, isolating device from network and other actions that require communication with the device may not work.

- **Inactive** - Devices that have stopped reporting to the Defender for Endpoint service.

You can also download the entire list in CSV format using the **Export** feature. For more information on filters, see [View and organize the Devices list](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview).

Note

Export the list in CSV format to display the unfiltered data. The CSV file will include all devices in the organization, regardless of any filtering applied in the view itself and can take a significant amount of time to download, depending on how large your organization is.

You can view the device details when you click on a misconfigured or inactive device.

## See also

- [Fix unhealthy sensors in Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/fix-unhealthy-sensors)
- [Client analyzer overview](https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer)
- [Run the client analyzer on Windows](https://learn.microsoft.com/en-us/defender-endpoint/run-analyzer-windows)
- [Data collection for advanced troubleshooting on Windows](https://learn.microsoft.com/en-us/defender-endpoint/data-collection-analyzer)
