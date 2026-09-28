<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicescopeparameter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceScopeParameter enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device scope configuration parameter. It will be expend in future to add more parameter. Eg: device scope parameter can be OS version, Disk Type, Device manufacturer, device model or Scope tag. Default value: scopeTag.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| none | 0 | Device Scope parameter is not set |
| scopeTag | 1 | use Scope Tag as parameter for the device scope configuration. |
| unknownFutureValue | 2 | Placeholder value for future expansion. |
