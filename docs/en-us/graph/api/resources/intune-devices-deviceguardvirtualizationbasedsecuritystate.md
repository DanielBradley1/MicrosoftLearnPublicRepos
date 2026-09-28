<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-deviceguardvirtualizationbasedsecuritystate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceGuardVirtualizationBasedSecurityState enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| running | 0 | Running |
| rebootRequired | 1 | Root required |
| require64BitArchitecture | 2 | 64 bit architecture required |
| notLicensed | 3 | Not licensed |
| notConfigured | 4 | Not configured |
| doesNotMeetHardwareRequirements | 5 | System does not meet hardware requirements |
| other | 42 | Other. Event logs in microsoft-Windows-DeviceGuard have more details. |
