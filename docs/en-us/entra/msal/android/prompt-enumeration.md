<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/prompt-enumeration -->
<!-- Sitemap-Last-Modified: 2024-02-07 -->

# Prompt Enum

In MSAL 1.0 the enumeration UIBehavior was renamed to Prompt to align with the OpenId Connect Spec regarding auth request. See: [Authentication Request](https://openid.net/specs/openid-connect-core-1_0.html#AuthRequest)

MSAL for Android supports the following values within the Prompt enumeration:

| Name | Description |
| --- | --- |
| SELECT\_ACCOUNT | Use when you want the user to be able to choose between accounts with which they have active sessions with the authority. |
| LOGIN | Use when you want the user to authenticate explicitly again. |
| CONSENT | Use when you want the user to explicitly consent again. Useful when you want the user to update a potentially existing record of consent to include additional scopes/permissions. |
| WHEN\_REQUIRED | Use when you want the authority to determine the correct behavior. Authenticate if no active sessions. Select account if multiple sessions. Consent if consent is required. |
