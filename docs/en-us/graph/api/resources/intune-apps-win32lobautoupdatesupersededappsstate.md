<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobautoupdatesupersededappsstate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# win32LobAutoUpdateSupersededAppsState enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains value for auto-update superseded apps.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| notConfigured | 0 | Indicates that the auto-update superseded apps state is not configured and the app will not auto-update the superseded apps. |
| enabled | 1 | Indicates that the auto-update superseded apps state is enabled and the app will auto-update the superseded apps if the superseded apps are installed on the device. |
| unknownFutureValue | 2 | Evolvable enumeration sentinel value. Do not use. |
