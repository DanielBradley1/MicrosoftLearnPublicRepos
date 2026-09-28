<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-windowsautopilotdeploymentstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsAutopilotDeploymentState enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Deployment states for Autopilot devices

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 | The deployment state is unknown. |
| success | 1 | The deployment succeeded. |
| inProgress | 2 | The deployment state is in progress. |
| failure | 3 | The deployment failed. |
| successWithTimeout | 4 | The deployment timed out but user clicked past failure. |
| notAttempted | 5 | The deployment was not run. |
| disabled | 6 | The deployment is disabled. |
| successOnRetry | 7 | The deployment succeeded after hitting an initial timeout failure. |
