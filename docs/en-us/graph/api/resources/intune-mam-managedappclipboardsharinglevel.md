<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappclipboardsharinglevel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAppClipboardSharingLevel enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents the level to which the device's clipboard may be shared between apps

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| allApps | 0 | Sharing is allowed between all apps, managed or not |
| managedAppsWithPasteIn | 1 | Sharing is allowed between all managed apps with paste in enabled |
| managedApps | 2 | Sharing is allowed between all managed apps |
| blocked | 3 | Sharing between apps is disabled |
