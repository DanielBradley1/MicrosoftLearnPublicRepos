<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnserviceexceptionaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# vpnServiceExceptionAction enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The VPN action to take for a specific service.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| forceTrafficViaVPN | 0 | Make all traffic from that service go through the VPN |
| allowTrafficOutside | 1 | Allow the service outside of the VPN |
| dropTraffic | 2 | Drop all traffic from the service |
