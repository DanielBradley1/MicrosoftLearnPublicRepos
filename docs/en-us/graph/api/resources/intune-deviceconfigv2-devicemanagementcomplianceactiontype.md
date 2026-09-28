<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcomplianceactiontype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementComplianceActionType enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Scheduled Action Type Enum

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| noAction | 0 | No Action |
| notification | 1 | Send Notification |
| block | 2 | Block the device in AAD |
| retire | 3 | Retire the device |
| wipe | 4 | Wipe the device |
| removeResourceAccessProfiles | 5 | Remove Resource Access Profiles from the device |
| pushNotification | 9 | Send push notification to device |
| remoteLock | 10 | Remotely lock the device |
