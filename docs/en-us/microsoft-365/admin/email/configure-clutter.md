<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/email/configure-clutter?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# Configure Microsoft 365 Clutter for your organization

As an admin, you might need to manage the Clutter feature in Microsoft 365. To turn the Clutter feature on or off for users in your organization, use Exchange PowerShell. \(Individuals can turn it on or off by using these instructions: [Turn off/on Clutter in Outlook](https://support.microsoft.com/office/a9c72a77-1bc4-40e6-ba6d-103c1d1aba4c)\).

For details on using Exchange PowerShell, see [Using PowerShell with Exchange Online](https://learn.microsoft.com/en-us/powershell/exchange/exchange-online-powershell) and [Connect to Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell). You need an account that has at least the [Exchange Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#exchange-administrator) role and the ability to connect to Exchange Online by using PowerShell.

## Turn on Clutter by using Exchange PowerShell

You can enable Clutter manually for a mailbox by running the [Set-Clutter](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/set-clutter) cmdlet. You can also view Clutter settings for mailboxes in your organization by running the [Get-Clutter](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-clutter) cmdlet.

Turn on Clutter for a single user named Allie Bellew:

`Set-Clutter -Identity "Allie Bellew" -Enable $true`

## Turn Clutter off by using Exchange PowerShell

You can disable Clutter manually for a mailbox by running the [Set-Clutter](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/set-clutter) cmdlet. You can also view **Clutter** settings for mailboxes in your organization by running the [Get-Clutter](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/get-clutter) cmdlet. For example, to turn off Clutter for a single user named Allie Bellew, run the following PowerShellcommand:

```PowerShell
Set-Clutter -Identity "Allie Bellew" -Enable $false`
```

If you use PowerShell to bulk create your users, run [Set-Clutter](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/set-clutter) against each user's mailbox to manage Clutter.

## How Clutter appears in Outlook on the web

As an admin, you can re-enable Clutter by using Exchange PowerShell. Focused Inbox is turned off and Clutter is active again.

### If you're using Outlook on the web with a Microsoft 365 Business Premium subscription

- If you currently have Clutter enabled:

  - Clutter settings appear.

- If you currently have Focused Inbox enabled:

  - Clutter settings don't appear.

- If Clutter and Focused Inbox are both disabled:

  - Both Clutter and Focused Inbox appear as options in your Mail Settings.

### If you're using Outlook.com

- If you currently have Clutter enabled:

  - Clutter settings appear.

- If you currently have Focused Inbox enabled:

  - Clutter settings don't appear.

- If Clutter and Focused Inbox are both disabled:

  - Both Clutter and Focused Inbox appear as options in your Mail Settings.

## Related content

- [Use Clutter to sort low priority messages in Outlook](https://support.microsoft.com/office/7b50c5db-7704-4e55-8a1b-dfc7bf1eafa0).
- [Use Clutter to sort low priority messages in OWA](https://support.microsoft.com/office/fe4d64ca-bf73-48f1-91b4-9a659e008bce).
