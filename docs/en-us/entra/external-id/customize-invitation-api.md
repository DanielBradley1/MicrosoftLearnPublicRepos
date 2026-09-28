<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customize-invitation-api -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# Microsoft Entra B2B collaboration API and customization

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

[With the Microsoft Graph REST API](https://learn.microsoft.com/en-us/graph/api/resources/invitation), you can customize the invitation process in a way that works best for your organization.

## Capabilities of the invitation API

The API offers the following capabilities:

1. The following JSON representation shows how to invite an external user with *any* email address.

   ```
   "invitedUserDisplayName": "Taylor",
   "invitedUserEmailAddress": "taylor@fabrikam.com"
   ```

2. Customize where you want your users to land after they accept their invitation.

   ```
   "inviteRedirectUrl": "https://myapps.microsoft.com/"
   ```

3. Choose to send the standard invitation mail through us.

   ```
   "sendInvitationMessage": true
   ```


   With a message to the recipient that you can customize.


   ```
   "customizedMessageBody": "Hello Sam, let's collaborate!"
   ```

4. And choose to cc: people you want to keep in the loop about your inviting this collaborator.
5. Or completely customize your invitation and onboarding workflow by choosing not to send notifications through Microsoft Entra ID.

   ```
   "sendInvitationMessage": false
   ```


   In this case, you get back a redemption URL from the API that you can embed in an email template, IM, or other distribution method of your choice.

6. Finally, if you're an admin, you can choose to invite the user as member.

   ```
   "invitedUserType": "Member"
   ```

## Determine if a user was already invited to your directory

You can use the invitation API to determine if a user already exists in your resource tenant. This can be useful when you're developing an app that uses the invitation API to invite a user. If the user already exists in your resource directory, they won't receive an invitation, so you can run a query first to determine whether the email already exists as a UPN or other sign-in property.

1. Make sure the user's email domain isn't part of your resource tenant's verified domain.
2. In the resource tenant, use the following get user query where 0 is the email address you're inviting:

   ```
   “userPrincipalName eq '0' or mail eq '0' or proxyAddresses/any(x:x eq 'SMTP:0') or signInNames/any(x:x eq '0') or otherMails/any(x:x eq '0')" 
   ```

## Authorization model

The API can be run in the following authorization modes:

### App + User mode

In this mode, whoever is using the API needs to have the permissions to be create B2B invitations.

### App only mode

In app only context, the app needs the User.Invite.All scope for the invitation to succeed.

For more information, see: [https://developer.microsoft.com/graph/docs/authorization/permission\_scopes](https://developer.microsoft.com/graph/docs/authorization/permission_scopes)

## PowerShell

You can use PowerShell to add and invite external users to an organization easily. Create an invitation using the cmdlet:

```powershell
New-MgInvitation
```

You can use the following options:

- -InvitedUserDisplayName
- -InvitedUserEmailAddress
- -SendInvitationMessage
- -InvitedUserMessageInfo

### Invitation status

After you send an external user an invitation, you can use the **Get-MgBetaUser** cmdlet to see if they've accepted it. The following properties of Get-MgBetaUser are populated when an external user is sent an invitation:

- **externalUserState** indicates whether the invitation is **PendingAcceptance** or **Accepted**.
- **externalUserStateChangeDateTime** shows the timestamp for the latest change to the **externalUserState** property.

You can use the **Filter** option to filter the results by **externalUserState**. The example below shows how to filter results to show only users who have a pending invitation. The example also shows the **Format-List** option, which lets you specify the properties to display.

```powershell
Get-MgBetaUser -Filter "externalUserState eq 'PendingAcceptance'" | Format-List -Property DisplayName,UserPrincipalName,externalUserState,externalUserStateChangeDateTime
```

Note

Make sure you have the latest version of the [Microsoft Graph PowerShell module](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview)

## See also

Check out the invitation API reference in [https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/invitation](https://learn.microsoft.com/en-us/graph/api/resources/invitation).

## Related content

- [What is Microsoft Entra B2B collaboration?](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b)
- [Add and invite guest users](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator)
- [The elements of the B2B collaboration invitation email](https://learn.microsoft.com/en-us/entra/external-id/invitation-email-elements)
