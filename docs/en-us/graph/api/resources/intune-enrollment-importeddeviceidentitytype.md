<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-importeddeviceidentitytype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# importedDeviceIdentityType enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 | Unknown value of importedDeviceIdentityType. |
| imei | 1 | Device Identity is of type imei. |
| serialNumber | 2 | Device Identity is of type serial number. |
| manufacturerModelSerial | 3 | Device Identity is of type manufacturer + model + serial number semi-colon delimited tuple with enforced order. |
