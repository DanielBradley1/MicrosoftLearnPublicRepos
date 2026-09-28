<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementassignmentlinktype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementAssignmentLinkType enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

DeviceAndAppManagementAssignmentLinkType indicates the type of target assignment to a payload. A target can be directly assigned to a payload or have an assignment based on its lineage.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 | Default. Indicates unknown link type. |
| direct | 1 | Indicates that a payload is a directly assigned to a target. |
| inherited | 2 | Indicates that a payload assignment is inherited from a target's lineage. |
| unknownFutureValue | 3 | Evolvable enumeration sentinel value. Do not use. |
