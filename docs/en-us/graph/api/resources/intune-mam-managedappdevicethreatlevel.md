<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdevicethreatlevel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAppDeviceThreatLevel enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The maxium threat level allowed for an app to be compliant.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| notConfigured | 0 | Value not configured |
| secured | 1 | Device needs to have no threat |
| low | 2 | Device needs to have a low threat. |
| medium | 3 | Device needs to have not more than medium threat. |
| high | 4 | Device needs to have not more than high threat |
