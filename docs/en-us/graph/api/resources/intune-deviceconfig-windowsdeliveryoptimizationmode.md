<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsdeliveryoptimizationmode?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsDeliveryOptimizationMode enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Delivery optimization mode for peer distribution

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| userDefined | 0 | Allow the user to set. |
| httpOnly | 1 | HTTP only, no peering |
| httpWithPeeringNat | 2 | OS default – Http blended with peering behind the same network address translator |
| httpWithPeeringPrivateGroup | 3 | HTTP blended with peering across a private group |
| httpWithInternetPeering | 4 | HTTP blended with Internet peering |
| simpleDownload | 99 | Simple download mode with no peering |
| bypassMode | 100 | Bypass mode. Do not use Delivery Optimization and use BITS instead |
