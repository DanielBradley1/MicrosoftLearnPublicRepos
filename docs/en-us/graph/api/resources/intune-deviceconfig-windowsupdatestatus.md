<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsupdatestatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsUpdateStatus enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows update for business configuration device states

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| upToDate | 0 | There are no pending updates, no pending reboot updates and no failed updates. |
| pendingInstallation | 1 | There are updates that’s pending installation which includes updates that are not approved. There are no Pending reboot updates, no failed updates. |
| pendingReboot | 2 | There are updates that requires reboot. There are not failed updates. |
| failed | 3 | There are updates failed to install on the device. |
