<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcontentscriptstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-09 -->

# mobileAppContentScriptState enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A list of possible script lifecycle states.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| commitPending | 0 | Indicates that the script content is in a pending state. |
| commitSuccess | 1 | Indicates that the script content is ready. |
| commitFailed | 2 | Indicates that the script is in an unusable state. |
| unknownFutureValue | 3 | Evolvable enumeration sentinel value. Do not use. |
