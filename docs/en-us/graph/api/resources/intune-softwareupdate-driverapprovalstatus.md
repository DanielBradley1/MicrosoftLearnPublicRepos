<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-driverapprovalstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# driverApprovalStatus enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

An enum type to represent approval status of a driver.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| needsReview | 0 | This indicates a driver needs IT admin's review. |
| declined | 1 | This indicates IT admin has declined a driver. |
| approved | 2 | This indicates IT admin has approved a driver. |
| suspended | 3 | This indicates IT admin has suspended a driver. |
