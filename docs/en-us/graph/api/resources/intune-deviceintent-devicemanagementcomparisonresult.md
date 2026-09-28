<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementcomparisonresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementComparisonResult enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Setting comparison result type

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 | Unknown setting comparison |
| equal | 1 | The setting values are equal |
| notEqual | 2 | The setting values are not equal |
| added | 3 | The setting is added |
| removed | 4 | The setting is removed |
