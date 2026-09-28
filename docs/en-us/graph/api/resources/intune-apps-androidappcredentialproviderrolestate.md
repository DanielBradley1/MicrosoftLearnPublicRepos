<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-androidappcredentialproviderrolestate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# androidAppCredentialProviderRoleState enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Android credential provider role state for apps.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| notConfigured | 0 | Default. Indicates the app's ability to act as a credential provider has not been configured. When set to 'notConfigured', the Android OS will determine whether the app is allowed to act as a credential provider or not. |
| allowed | 1 | Indicates the app is allowed to act as a credential provider. |
| unknownFutureValue | 2 | Evolvable enumeration sentinel value. Do not use. |
