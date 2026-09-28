<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsdevicetype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# windowsDeviceType enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for Windows device type. Multiple values can be selected. Default value is `none`.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| none | 0 | No device types supported. Default value. |
| desktop | 1 | Indicates support for Desktop Windows device type. |
| mobile | 2 | Indicates support for Mobile Windows device type. |
| holographic | 4 | Indicates support for Holographic Windows device type. |
| team | 8 | Indicates support for Team Windows device type. |
| unknownFutureValue | 16 | Evolvable enumeration sentinel value. Do not use. |
