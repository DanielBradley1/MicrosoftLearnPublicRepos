<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-appinstallcontroltype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# appInstallControlType enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

App Install control Setting

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| notConfigured | 0 | Not configured |
| anywhere | 1 | Turn off app recommendations |
| storeOnly | 2 | Allow apps from Store only |
| recommendations | 3 | Show me app recommendations |
| preferStore | 4 | Warn me before installing apps from outside the Store |
