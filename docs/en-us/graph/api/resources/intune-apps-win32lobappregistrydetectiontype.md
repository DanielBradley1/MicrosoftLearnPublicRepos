<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappregistrydetectiontype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# win32LobAppRegistryDetectionType enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains all supported registry data detection type.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| notConfigured | 0 | Not configured. |
| exists | 1 | The specified registry key or value exists. |
| doesNotExist | 2 | The specified registry key or value does not exist. |
| string | 3 | String value type. |
| integer | 4 | Integer value type. |
| version | 5 | Version value type. |
