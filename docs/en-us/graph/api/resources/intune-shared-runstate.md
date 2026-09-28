<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-runstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# runState enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Indicates the type of execution status of the device management script.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 | Unknown result. |
| success | 1 | Script is run successfully. |
| fail | 2 | Script failed to run. |
| scriptError | 3 | Discovery script hits error. |
| pending | 4 | Script is pending to execute. |
| notApplicable | 5 | Script is not applicable for this device. |
