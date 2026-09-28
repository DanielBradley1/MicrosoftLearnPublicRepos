<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-invite-powershell -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# Quickstart: Add a guest user with PowerShell

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

There are many ways to invite external partners to your apps and services with Microsoft Entra B2B collaboration. In the previous quickstart, you saw how to add guest users directly in the Microsoft Entra admin center. You can also use PowerShell to add guest users, either one at a time or in bulk. In this quickstart, you use the `New-MgInvitation` command to add one guest user to your Microsoft Entra tenant.

This article explains how to invite guest users with Microsoft Graph PowerShell. You can also manage guest users with [Microsoft Entra PowerShell](https://learn.microsoft.com/en-us/powershell/entra-powershell/manage-guest-users).

## Prerequisites

To complete the scenario in this quickstart, you need:

- An Azure subscription. If you don't have an Azure subscription, create a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.
- A role that allows you to create users in your tenant directory, such as at least a [Guest Inviter role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#guest-inviter) or a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
- Install the [Microsoft Graph Identity Sign-ins module](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.signins/?viewFallbackFrom=graph-powershell-beta&preserve-view=true&view=graph-powershell-1.0) \(Microsoft.Graph.Identity.SignIns\) and the [Microsoft Graph Users module](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.users/?viewFallbackFrom=graph-powershell-beta&preserve-view=true&view=graph-powershell-1.0) \(Microsoft.Graph.Users\). You can use the `#Requires` statement to prevent running a script unless the required PowerShell modules are met.

```powershell
#Requires -Modules Microsoft.Graph.Identity.SignIns, Microsoft.Graph.Users
```

- Get a test email account. You need a test email account that you can send the invitation to. The account must be from outside your organization. You can use any type of account, including a social account such as a Gmail.com or Outlook.com address.

Note

This article uses Microsoft Graph PowerShell, which replaces the retired Azure AD and MSOnline PowerShell modules.

## Sign in to your tenant

Run the following command to connect to your tenant:

```powershell
Connect-MgGraph -Scopes 'User.Invite.All','User.Read.All'
```

When prompted, enter your credentials.

## Send an invitation

1. To send an invitation to your test email account, run the following PowerShell command \(replace **"Henry Ross"** and **henry@contoso.com** with your test email account name and email address\):

   ```powershell
   New-MgInvitation -InvitedUserDisplayName "Henry Ross" -InvitedUserEmailAddress henry@contoso.com -InviteRedirectUrl "https://myapplications.microsoft.com" -SendInvitationMessage:$true
   ```

2. The command sends an invitation to the email address specified. Check the output, which should look similar to the following example:

   ```Output
   Id                                   InviteRedeemUrl                                                                                                   
   --                                   ---------------                                                                                                   
   00aa00aa-bb11-cc22-dd33-44ee44ee44ee https://login.microsoftonline.com/redeem?...
   ```

## Verify the user exists in the directory

1. To verify that the invited user was added to Microsoft Entra ID, run the following command \(replace **henry@contoso.com** with your invited email\):

   ```powershell
   Get-MgUser -Filter "Mail eq 'henry@contoso.com'"
   ```

2. Check the output to make sure the user you invited is listed, with a user principal name \(UPN\) in the format *emailaddress*#EXT#@*domain*. For example, *henry\_contoso.com#EXT#@fabrikam.onmicrosoft.com*, where fabrikam.onmicrosoft.com is the organization from which you sent the invitations.

   ```Output
   Id                                   DisplayName              Mail                           UserPrincipalName        
   --                                   -----------              ----                           -----------------               
   00aa00aa-bb11-cc22-dd33-44ee44ee44ee Henry Ross               henry@contoso.com              henry_contoso.com#EXT#@fabrikam.onmicrosoft.com
   ```

## Clean up resources

When no longer needed, you can delete the test user account in the directory. Run the following command to delete a user account:

```powershell
Remove-MgUser -UserId '<String>'
```

For example:

```powershell
Remove-MgUser -UserId 'henry_contoso.com#EXT#@fabrikam.onmicrosoft.com'
```

Or

```powershell
Remove-MgUser -UserId '00aa00aa-bb11-cc22-dd33-44ee44ee44ee'
```

## Next steps

In this quickstart, you invited and added a single guest user to your directory by using PowerShell. You can also invite a guest user by using the [Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-add-guest-users-portal). Additionally, you can [invite guest users in bulk by using PowerShell](https://learn.microsoft.com/en-us/entra/external-id/tutorial-bulk-invite).
