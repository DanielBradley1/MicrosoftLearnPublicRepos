<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/require-scoped-access-to-files-and-sites-for-hpa-applications?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Require scoped access to files and sites for High-Privileged-Access applications

This setting blocks third-party applications that use High-Privileged-Access access \(HPA\) permissions to files and sites in SharePoint and OneDrive unless their access is explicitly scoped. High-Privileged-Access permissions grant broad tenant wide access to content, which can significantly increase security risk if an application is compromised. Enabling this control ensures that third-party apps either use limited, scoped permissions or are explicitly approved by an administrator.

This setting extends the protections already applied to Microsoft first party apps by bringing the same awareness and enforcement to third-party applications as part of Baseline Security Mode.

You must be a member of the [SharePoint Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#sharepoint-administrator) role to be able to configure this setting.

## Why this setting matters

Applications with High-Privileged-Access permissions operate with extensive access to organizational data and often run without direct user interaction. If such an application is misconfigured, abused, or compromised, it can lead to widespread data exposure.

This setting helps reduce that risk in several keyways:

- **Limits exposure from high-impact permissions** High-Privileged-Access permissions- such as access to all files or all sites- allow applications to read or modify content across the tenant. Requiring scoped access reduces the potential blast radius by ensuring apps can only access specific files or sites.
- **Protects against Third-Party app compromise** Third-Party apps are outside Microsoft's direct control and may follow different security practices. Blocking unscoped High-Privileged-Access access prevents these apps from becoming a single point of failure for tenant wide data security.
- **Aligns with least-privilege principles** Scoped access ensures applications request only the minimum permissions required for their functionality, improving governance and reducing unnecessary data access.
- **Provides visibility before enforcement** Reporting surfaces which Third-Party apps currently use High-Privileged-Access permissions, helping admins understand impact and make informed decisions before enforcing restrictions. This model allows organizations to progressively enforce scoped access, balancing security improvements with operational continuity.
