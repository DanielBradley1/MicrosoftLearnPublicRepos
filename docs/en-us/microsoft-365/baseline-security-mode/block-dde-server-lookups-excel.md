<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-dde-server-lookups-excel?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Block DDE server lookups in Excel

This setting blocks [Dynamic Data Exchange \(DDE\) server lookups in Microsoft Excel](https://learn.microsoft.com/en-us/windows/win32/dataxchg/about-dynamic-data-exchange). DDE is a legacy Windows technology that allows Excel to retrieve data from external applications through inter process communication. While designed for legitimate data exchange, attackers have abused DDE to run malicious commands or expose data without relying on macros.

When enabled, Excel no longer queries or connects to DDE servers, helping reduce the risk of malicious code execution or unintended data exposure. This setting is recommended and marked at risk because [DDE server lookups](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365-apps/excel/security-settings) expand the attack surface for document based threats.

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

## Why this setting matters

DDE operates outside modern security controls and trust boundaries, making it attractive for abuse in phishing and malware campaigns.

Blocking DDE server lookups helps mitigate these risks:

- **Reduces document based attack vectors** Attackers can exploit DDE lookups to run harmful commands or retrieve malicious content when a user opens a crafted Excel file- often without macros.
- **Prevents automatic access to external data sources** DDE allows Excel to discover and communicate with running external applications. Blocking lookups stops Excel from querying these sources through DDE.
- **Limits reliance on legacy technologies** DDE is an older protocol that doesn't align with modern security practices. Disabling server lookups encourages safer alternatives for data integration.
- **Improves visibility into potential impact** The admin center surfaces users and files currently involved in DDE server lookups, allowing admins to assess impact before enforcing the policy.

## How this setting works

When this setting is enabled:

- **Excel blocks DDE server lookups**, preventing Excel from querying or communicating with DDE servers for external data.
- **Existing DDE based workflows may stop functioning**, particularly scenarios that rely on automatic data retrieval from other applications.
- **Admins can review impacted users and files** directly in the admin center to understand who is using DDE server lookups.
- **A detailed CSV report is available for download**, making it easier to audit usage and plan remediation.
- **Safer alternatives remain available**, allowing organizations to reduce risk while modernizing data exchange patterns.
