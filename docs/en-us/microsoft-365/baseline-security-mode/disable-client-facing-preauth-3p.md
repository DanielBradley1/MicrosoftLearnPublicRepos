<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/disable-client-facing-preauth-3p?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Disable client facing preauthenticated URLs for Third-Party \(3P\) applications

This setting prevents third-party applications from using preauthenticated \(TempAuth\) URLs to access OneDrive and SharePoint files. Preauthenticated URLs embed short-lived tokens directly in the URL, allowing applications to download or preview content without completing full authentication. While originally intended for convenience, this pattern no longer meets modern security expectations and increases the risk of unauthorized access if the URL is leaked or intercepted. Enabling this setting ensures that external or untrusted apps must always authenticate properly before accessing Microsoft 365 files. This setting reduces exposure while still allowing admins to grant exceptions when required.

You must be a member of the [SharePoint Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) role to be able to configure this setting.

## Why this setting matters

Apps that rely on pre authenticated URLs can access files in OneDrive or SharePoint without additional authentication, which raises several security concerns:

- **Higher risk of unauthorized access** Because preauthenticated tokens are embedded directly in the URL, any party that obtains the link- through logs, referrals, browser history, or malicious interception- can use it to retrieve the associated file. This bypasses the protections provided by modern authentication flows.
- **Misuse by compromised or unverified applications** Third-Party applications are more likely to depend on legacy authentication patterns. If such an app is compromised, preauthenticated URLs can be exploited to pull data without user interaction, making it difficult for organizations to detect or contain misuse.
- **Potential disruption for apps dependent on preauthenticated URLs** Apps that currently use preauthenticated URLs may lose functionality or fail to connect once the setting is enabled. Admins should review the list of impacted apps \(via telemetry\) and selectively exempt only those apps that require continued access.
- **Strengthening your security posture through full authentication** Blocking preauthenticated URLs for 3P apps ensures file access requires full authentication and authorization- aligning with Zero-Trust standards and reducing reliance on inherently insecure URL-embedded tokens.

This setting aligns with broader baseline security mode efforts to eliminate insecure legacy authentication patterns and ensure that file access always occurs through verified, authenticated channels.
