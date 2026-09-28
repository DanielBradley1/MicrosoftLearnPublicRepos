<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceguardlocalsystemauthoritycredentialguardtype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceGuardLocalSystemAuthorityCredentialGuardType enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Possible values of Credential Guard settings.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| notConfigured | 0 | Turns off Credential Guard remotely if configured previously without UEFI Lock. |
| enableWithUEFILock | 1 | Turns on Credential Guard with UEFI lock. |
| enableWithoutUEFILock | 2 | Turns on Credential Guard without UEFI lock. |
| disable | 3 | Disables Credential Guard. This is the default OS value. |
