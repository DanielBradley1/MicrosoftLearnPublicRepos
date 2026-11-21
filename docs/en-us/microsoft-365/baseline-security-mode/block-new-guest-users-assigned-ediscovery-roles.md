<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-new-guest-users-assigned-ediscovery-roles?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Block new guest accounts from being assigned eDiscovery roles

eDiscovery roles grant the ability to search for and export data from Microsoft 365 sources- making them high privilege compliance roles. To reduce risk, this setting prevents new guest accounts from being assigned any eDiscovery related roles.

When enabled:

- New guest accounts can't be added to eDiscovery roles by eDiscovery admins.
- Existing guest accounts who already have eDiscovery roles keep their access.

You must be a member of the [Global Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) role to configure this setting.

## How this setting works

When this setting is turned on:

- New guest accounts can't be assigned any of the following roles:

  - eDiscovery Manager
  - eDiscovery Administrator
  - Reviewer
  - Compliance Administrator \(when tied to eDiscovery permissions\)

- Existing guest accounts with previously assigned eDiscovery roles aren't modified.
- Admins can still manually evaluate and grant permissions to a guest account if there's a legitimate business justification.

## Why this setting matters

Guest accounts often have lower assurance and may not meet organizational compliance standards. Because eDiscovery permissions enable access to sensitive data exports, Microsoft recommends not assigning eDiscovery roles to guest accounts.
