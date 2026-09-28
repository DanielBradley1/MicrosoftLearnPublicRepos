<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentstate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# enrollmentState enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 | Device enrollment state is unknown |
| enrolled | 1 | Device is Enrolled. |
| pendingReset | 2 | Enrolled but it's enrolled via enrollment profile and the enrolled profile is different from the assigned profile. |
| failed | 3 | Not enrolled and there is enrollment failure record. |
| notContacted | 4 | Device is imported but not enrolled. |
