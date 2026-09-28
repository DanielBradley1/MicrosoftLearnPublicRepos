<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileaccountuse?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidWorkProfileAccountUse enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

An enum representing possible values for account use in work profile.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| allowAllExceptGoogleAccounts | 0 | Allow additon of all accounts except Google accounts in Android Work Profile. |
| blockAll | 1 | Block any account from being added in Android Work Profile. |
| allowAll | 2 | Allow addition of all accounts \(including Google accounts\) in Android Work Profile. |
| unknownFutureValue | 3 | Unknown future value for evolvable enum patterns. |
