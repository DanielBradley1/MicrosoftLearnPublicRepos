<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerwifisecuritytype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidDeviceOwnerWiFiSecurityType enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Wi-Fi Security Types for Android Device Owner.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| open | 0 | Open \(No Authentication\). |
| wep | 1 | WEP Encryption. |
| wpaPersonal | 2 | WPA-Personal/WPA2-Personal. |
| wpaEnterprise | 4 | WPA-Enterprise/WPA2-Enterprise. Must use AndroidDeviceOwnerEnterpriseWifiConfiguration type to configure enterprise options. |
