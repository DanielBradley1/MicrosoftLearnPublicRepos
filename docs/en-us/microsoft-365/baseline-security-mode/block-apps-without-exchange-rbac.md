<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-apps-without-exchange-rbac?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Detect incorrect RBAC setup in Exchange

This report provides a list of applications that do not have the Exchange App RBAC setup correctly and therefore rely on Entra permissions for accessing Exchange. We recommend removing unscoped permissions granted within Entra and replacing them with scoped permissions using [Role Based Access Control \(RBAC\) for Applications](https://learn.microsoft.com/en-us/exchange/permissions-exo/application-rbac).

Applications without scoped permissions can access all mailboxes and resources in the organization, depending on the permissions used. This broad level of access increases the risk of data leaks or misuse if the app is compromised or misconfigured.

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) or [Exchange administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#exchange-administrator) to be able to configure this setting.

## Why this setting matters

Applications without scoped permissions can access every mailbox in the organization. If such application is compromised or misconfigured, it can result in widespread data leaks or unauthorized access.

Setting up Exchange Application RBAC helps to address these risks:

- **Reduces tenant-wide exposure**  
  App-only permissions granted through Entra \(such as Mail.Read or Calendars.Read\) apply to all mailboxes by default. Exchange App RBAC adds a scope so applications can access only a defined set of users.
- **Limits the impact of compromised apps**  
  If an application is breached, scoped access ensures the impact is contained to the mailboxes explicitly assigned to the app, rather than the entire organization.

## How this setting works

When this setting is enabled:

- The admin center surfaces report of applications accessing Exchange that rely on Entra permissions. This allows admins to have visibility and plan remediation.
- Tenant admins can download a CSV report that identifies the applications and provides the reason each application was included.

Note

Microsoft first-party applications are not affected by this setting and continue to operate as designed.
