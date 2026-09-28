<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentringstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementDeploymentRingState enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents the status of a deployment ring.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| notActivated | 0 | Deployment Ring is not activated. |
| activating | 1 | Deployment Ring is activating. |
| canceled | 2 | Deployment Ring has been canceled. |
| paused | 3 | Deployment Ring has been paused. |
| activated | 4 | Deployment Ring has been activated. |
| error | 5 | Deployment Ring has errors. |
| unknownFutureValue | 6 | Unknown future value. |
