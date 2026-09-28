<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/set-up-your-account-places-admin -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Set up your account as a Places Admin

## Prerequisites

You need a Places Administrator Exchange Role assigned from the M365 Admin Center.

## Tools

You need **PowerShell 7** version 7.4.0 or later. You can't use Windows PowerShell to manage Microsoft Places. Go to [Installing PowerShell](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell) to download the latest version of PowerShell.

You also need the following PowerShell modules:

- [Exchange Online](https://learn.microsoft.com/en-us/powershell/exchange/exchange-online-powershell-v2)
- [Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/teams-powershell-install)
- Microsoft Places

Verify that you have the latest **MicrosoftPlaces** PowerShell module installed. Use the following command to install or update it:

```powershell
Install-Module -Name MicrosoftPlaces -Force
```

## Permissions

Places supports three built-in roles: Places Administrator, Places Building Administrator, and Places Desk Administrator. For a detailed overview of each role, refer to [Enable others as Places administrators](https://learn.microsoft.com/en-us/microsoft-365/places/day-to-day-admin/enable-others-as-places-admins).

You need two Exchange Online management roles: **TenantPlacesManagement** \(to manage Places\) and **MailRecipient** \(to manage users and mailboxes\).

Alternatively, the [Exchange administrator role](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-exchange-online-admin-role) has the necessary permissions to manage mail recipient objects, and accounts with the Exchange administrator role often also have the **TenantPlacesManagement** role assigned.

If your account doesn't have the **TenantPlacesManagement** role assigned, you can assign it using PowerShell:

```powershell
New-ManagementRoleAssignment -Role TenantPlacesManagement -User <UPN>
```

Another option is to create a new role group called **Microsoft Places Management**, grant the **TenantPlacesManagement** and **MailRecipient** roles to it, and then assign users to the new role group.

You can also use the Organization Management role group, but users in this group are overprivileged for managing Places.
