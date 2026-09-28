<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/reset-redemption-status -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# Reset the redemption status for a guest user in Microsoft Entra External ID

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

In this article, you'll learn how to update the [guest user's](https://learn.microsoft.com/en-us/entra/external-id/user-properties) sign-in information after they've redeemed your invitation for B2B collaboration. There might be times when you'll need to update their sign-in information, for example when:

- The user wants to sign in using a different email and identity provider
- The account for the user in their home tenant has been deleted and re-created
- The user has moved to a different company, but they still need the same access to your resources
- The user’s responsibilities have been passed along to another user

In the past, to manage these scenarios, you had to manually delete the guest user's account from your directory and reinvite the user. Now you can use the Microsoft Entra admin center, PowerShell, or the Microsoft Graph invitation API to reset the user's redemption status and reinvite the user while keeping the user's object ID, group memberships, and app assignments. When the user redeems the new invitation, the user principal name \(UPN\) doesn't change, but the user's sign-in name changes to the new email. The user can then sign in by using the new email or an email you've added to the `otherMails` property of the user object.

## Required Microsoft Entra roles

To reset a user's redemption status, you'll need one of the following roles assigned at the directory scope:

- [Helpdesk Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#helpdesk-administrator) \(least privileged\)
- [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator)

## Use the Microsoft Entra admin center to reset redemption status

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users**.
3. In the list, select the user's name to open their user profile.
4. \(Optional\) If the user wants to sign in using a different email:

   1. Select the **Edit properties** icon.
   2. On the **All** tab or on the **Contact Information** tab, scroll to **Email** and type the new email.
   3. Next to **Other emails**, select **Add or edit other emails**. Select **Add**, type the new email, and select **Save**.
   4. Select the **Save** button at the bottom of the page to save all changes.

5. On the **Overview** tab, under **My Feed**, select the **Reset redemption status** link in the **B2B collaboration** tile.

   [![Screenshot of a guest user profile in the Microsoft Entra admin center, with the Reset redemption status link highlighted in the B2B collaboration tile on the Overview tab.](https://learn.microsoft.com/en-us/entra/external-id/media/reset-redemption-status/user-profile-b2b-collaboration.png)](https://learn.microsoft.com/en-us/entra/external-id/media/reset-redemption-status/user-profile-b2b-collaboration.png#lightbox)
6. Under **Reset redemption status**, select **Reset**.

   ![Screenshot of the Reset redemption status pane showing the Reset action that resends the invitation while keeping the guest user object.](https://learn.microsoft.com/en-us/entra/external-id/media/reset-redemption-status/reset-status.png)

## Use PowerShell or Microsoft Graph API to reset redemption status

### Reset the email address used for sign-in

If a user wants to sign in using a different email:

1. Make sure the new email address is added to the `mail` or `otherMails` property of the user object.
2. Replace the email address in the `InvitedUserEmailAddress` property with the new email address.
3. Use one of the methods below to reset the user's redemption status.

Note

- When you're resetting the user's email address to a new address, we recommend setting the `mail` property. This way the user can redeem the invitation by signing into your directory in addition to using the redemption link in the invitation.
- For app-only calls, the redemption status can't be reset if there are any roles assigned to the target user account.

### Use PowerShell to reset redemption status

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser
Connect-MgGraph -Scopes "User.Invite.All","User.ReadWrite.All"

$user = Get-MgUser -Filter "startsWith(mail, 'john.doe@fabrikam.net')"
New-MgInvitation `
    -InvitedUserEmailAddress $user.Mail `
    -InviteRedirectUrl "https://myapps.microsoft.com" `
    -ResetRedemption `
    -SendInvitationMessage `
    -InvitedUser $user
```

### Use Microsoft Graph API to reset redemption status

To use the [Microsoft Graph invitation API](https://learn.microsoft.com/en-us/graph/api/resources/invitation), set the `resetRedemption` property to `true` and specify the new email address in the `invitedUserEmailAddress` property.

```json
POST https://graph.microsoft.com/v1.0/invitations  
Authorization: Bearer eyJ0eX...  
Content-Type: application/json  
{  
   "invitedUserEmailAddress": "<<external email>>",  
   "sendInvitationMessage": true,  
   "invitedUserMessageInfo": {  
      "messageLanguage": "en-US",  
      "ccRecipients": [  
         {  
            "emailAddress": {  
               "name": null,  
               "address": "<<optional additional notification email>>"  
            }  
         } 
      ],  
      "customizedMessageBody": "<<custom message>>"  
},  
"inviteRedirectUrl": "https://myapps.microsoft.com?tenantId=<tenant-id>",  
"invitedUser": {  
   "id": "<<ID for the user you want to reset>>"  
}, 
"resetRedemption": true 
}
```

## Next step

- [Properties of a Microsoft Entra B2B guest user](https://learn.microsoft.com/en-us/entra/external-id/user-properties)
