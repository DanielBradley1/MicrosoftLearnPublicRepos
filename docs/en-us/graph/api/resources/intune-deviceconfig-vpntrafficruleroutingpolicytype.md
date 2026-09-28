<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpntrafficruleroutingpolicytype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# vpnTrafficRuleRoutingPolicyType enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Specifies the routing policy for a VPN traffic rule.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| none | 0 | No routing policy specified. |
| splitTunnel | 1 | Network traffic for the specified app will be routed through the VPN. |
| forceTunnel | 2 | All network traffic will be routed through the VPN. |
