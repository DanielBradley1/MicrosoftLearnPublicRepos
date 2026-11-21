<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-connection-untrusted-microsoft-query-files?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Block connection of untrusted Microsoft Query files

This setting helps protect your organization from unsafe external data connections in Excel. It applies to Microsoft Query files, such as .iqy, .oqy, .dqy, and .rqy, that have the mark of the web \(MOTW\) metadata identifier and can contain links to external data sources or include command strings that may expose users to security risks. It doesn't apply to other file formats. Enabling this setting ensures that only trusted Query files can establish data connections.

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

## Why this setting matters

Untrusted Query files can:

- Connect to unverified external systems
- Run unsafe queries or commands
- Introduce data leakage or unwanted data manipulation
- Bypass organizational security controls if left unrestricted

Blocking these connections helps protect both users and data by enforcing modern, trusted workflows for external data access.

## How this setting works

When enabled, this control:

- Blocks untrusted Microsoft Query files from connecting to data sources in Excel
- Prevents users from opening or launching *.iqy*, *.oqy*, *.dqy*, or *.rqy* files that were downloaded from the internet or another potentially unsafe source.
- Reduces the likelihood of malicious or tampered query files exposing or extracting data

Untrusted files are prevented from connecting, and users receive a notification explaining why the file was blocked.

## Use Cloud Policy service

You can also make changes to the policy settings directly using the [Cloud Policy service](https://config.office.com/). Set the **Always prevent untrusted Microsoft Query files from opening** policy as not configured to revert to the default behavior.
