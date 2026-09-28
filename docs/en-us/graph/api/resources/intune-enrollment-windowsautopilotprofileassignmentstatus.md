<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotprofileassignmentstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsAutopilotProfileAssignmentStatus enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 | Unknown assignment status |
| assignedInSync | 1 | Assigned successfully in Intune and in sync with Windows auto pilot program |
| assignedOutOfSync | 2 | Assigned successfully in Intune and not in sync with Windows auto pilot program |
| assignedUnkownSyncState | 3 | Assigned successfully in Intune and either in-sync or out of sync with Windows auto pilot program |
| notAssigned | 4 | Not assigned |
| pending | 5 | Pending assignment |
| failed | 6 | Assignment failed |
