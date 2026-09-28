<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnectorstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementDomainJoinConnectorState enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The ODJ request states.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| active | 0 | Connector is actively pinging Intune. |
| error | 1 | There is no heart-beat from connector from last one hour. |
| inactive | 2 | There is no heart-beat from connector from last 5 days. |
