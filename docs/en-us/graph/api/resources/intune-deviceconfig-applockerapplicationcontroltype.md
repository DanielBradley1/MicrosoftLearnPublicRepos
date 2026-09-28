<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applockerapplicationcontroltype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# appLockerApplicationControlType enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Possible values of AppLocker Application Control Types

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| notConfigured | 0 | Device default value, no Application Control type selected. |
| enforceComponentsAndStoreApps | 1 | Enforce Windows component and store apps. |
| auditComponentsAndStoreApps | 2 | Audit Windows component and store apps. |
| enforceComponentsStoreAppsAndSmartlocker | 3 | Enforce Windows components, store apps and smart locker. |
| auditComponentsStoreAppsAndSmartlocker | 4 | Audit Windows components, store apps and smart locker​. |
