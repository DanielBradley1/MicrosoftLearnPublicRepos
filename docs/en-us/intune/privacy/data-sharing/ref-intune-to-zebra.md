<!-- Source: https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ref-intune-to-zebra -->
<!-- Sitemap-Last-Modified: 2026-04-09 -->

# Data Intune sends to Zebra

When Zebra LifeGuard Over-the-Air \(LG OTA\) is enabled for your tenant, Microsoft Intune establishes a connection with Zebra and shares the following data with Zebra:

The following table lists the data that Microsoft Intune sends to Google when device management is enabled on a device:

| Data sent to Zebra | Used for | Example |
| --- | --- | --- |
| Serial number | Used to prove ownership of device against a known service contract with Zebra, determine current state of the device, and for the Android update process. | Unique identifier, example format: 124411614K0593 |
| Deployment settings | Used to deliver Android updates. | <li>Device Model: TC8300</li><br><br><li>Update type: Custom Time zone offset in minutes: 300</li><br><br><li>BSP (Board Support Package): 11.15.05.00</li><br><br><li>OS Version: 11</li><br><br><li>Patch Number: U20</li><br><br><li>Schedule mode: Latest</li><br><br><li>Schedule duration in days: 20</li><br><br><li>Download network type: Wifi</li><br><br><li>Download start date and time:</li><br><br><li>2022-03-25T15:04:51.8607086Z</li><br><br><li>Installation start date and time:</li><br><br><li>2022-03-25T15:04:51.8607086Z</li><br><br><li>Installation window start time: 19:00:00</li><br><br><li>Installation window end time: 19:00:00</li><br><br><li>Minimum Battery level percentage: 30</li><br><br><li>Require device to be on charger: true</li> |

To stop using Zebra services with Microsoft Intune and delete the data, you must both disconnect from Zebra LifeGuard OTA in Microsoft Intune, and also delete the data from your Zebra account by filing a customer request with Zebra.
