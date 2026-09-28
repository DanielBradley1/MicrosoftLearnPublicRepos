<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceregistrationstate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceRegistrationState enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device registration status.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| notRegistered | 0 | The device is not registered. |
| registered | 2 | The device is registered. |
| revoked | 3 | The device has been blocked, wiped or retired. |
| keyConflict | 4 | The device has a key conflict. |
| approvalPending | 5 | The device is pending approval. |
| certificateReset | 6 | The device certificate has been reset. |
| notRegisteredPendingEnrollment | 7 | The device is not registered and pending enrollment. |
| unknown | 8 | The device registration status is unknown. |
