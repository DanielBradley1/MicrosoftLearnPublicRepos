<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-insecure-protocols-file-opens?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-16 -->

# Block insecure protocols for file opens in Microsoft 365 apps

As a Microsoft 365 admin, you want to protect and secure your business environment. **Baseline security mode** helps you protect and secure your organization.

Hypertext Transfer Protocol \(HTTP\) and File Transfer Protocol \(FTP\) are outdated protocols that can expose sensitive data because they transmit information in plain text. Blocking file opens using these protocols helps prevent attackers from intercepting credentials or other confidential data during file access.

When this setting is turned on, users will be prevented from opening files from locations that use HTTP or FTP. Users will not be able to override this configuration in **Trust Center**. This helps enforce secure data transmission practices and reduces exposure to adversary-in-the-middle attacks. If you need to revert to the default behavior, you can turn off this setting directly in the Microsoft 365 admin center.

Note

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

## Turn off setting in the Microsoft 365 admin center

1. Go to the Microsoft 365 admin center at [https://admin.cloud.microsoft](https://go.microsoft.com/fwlink/p/?linkid=2024339) and select Org settings.
2. Select Baseline Security Mode, find the **Block insecure protocols for file opens** setting, and switch the toggle to **Off**.

## Use Office Cloud Policy service

Alternatively, you can make changes to the policy setting directly using the [Office Cloud Policy service](https://config.office.com/). Set the **Block Insecure Protocols** policy as not configured to revert to the default behavior.
