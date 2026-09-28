<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/redemption-experience -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# B2B collaboration invitation redemption

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

This article explains the Microsoft Entra B2B invitation redemption process for guest users, including how they access your resources and complete the required consent steps. Whether you send an invitation email or provide a direct link, guests are guided through a secure sign-in and consent process to ensure compliance with your organization’s privacy terms and [terms of use](https://learn.microsoft.com/en-us/entra/identity/conditional-access/terms-of-use).

When you add a guest user to your directory, the guest user account has a consent status \(viewable in PowerShell\) that's initially set to **PendingAcceptance**. This setting remains until the guest accepts your invitation and agrees to your privacy policy and terms of use. After that, the consent status changes to **Accepted**, and the consent pages are no longer presented to the guest.

Note

B2B invitation emails originating from Onmicrosoft default domains are subject to Exchange Online sending limits. See [Limiting Onmicrosoft Domain Usage for Sending Emails](https://learn.microsoft.com/en-us/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits) for more information. Consider updating to a custom domain if you need higher limits. For more information see, [Add your custom domain name to your tenant](https://learn.microsoft.com/en-us/entra/fundamentals/add-custom-domain).

## Redemption process and sign-in through a common endpoint

Guest users can now sign in to your multitenant or Microsoft first-party apps through a common endpoint \(URL\), for example `https://myapps.microsoft.com`. Previously, a common URL would redirect a guest user to their home tenant instead of your resource tenant for authentication, so a tenant-specific link was required \(for example `https://myapps.microsoft.com/?tenantid=<tenant id>`\). Now the guest user can go to the application's common URL, choose **Sign-in options**, and then select **Sign in to an organization**. The user then types the domain name of your organization.

![Screenshot of the Microsoft Entra B2B invitation redemption flow diagram.](https://learn.microsoft.com/en-us/entra/external-id/media/redemption-experience/common-endpoint-flow-small.png)

The user is then redirected to your tenant-specific endpoint, where they can either sign in with their email address or select an identity provider you configured.

## Redemption process through a direct link

As an alternative to the invitation email or an application's common URL, give a guest a direct link to your app or portal. First, add the guest user to your directory via the [Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-add-guest-users-portal) or [PowerShell](https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-invite-powershell). Then use any of the [customizable ways to deploy applications to users](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/end-user-experiences), including direct sign-on links. When a guest uses a direct link instead of the invitation email, the link still guides them through the first-time consent experience.

Note

A direct link is tenant-specific. In other words, it includes a tenant ID or verified domain so the guest can be authenticated in your tenant, where the shared app is located. Here are some examples of direct links with tenant context:

- Apps access panel: `https://myapps.microsoft.com/?tenantid=<tenant id>`
- Apps access panel for a verified domain: `https://myapps.microsoft.com/<;verified domain>`
- Microsoft Entra admin center: `https://entra.microsoft.com/<tenant id>`
- Individual app: see how to use a [direct sign-on link](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/end-user-experiences#direct-sign-on-links)

Here are some things to note about using a direct link versus an invitation email:

- **Email aliases:** Guests who use an alias of the email address that was invited need an email invitation. \(An alias is another email address associated with an email account.\) The user must select the redemption URL in the invitation email.
- **Conflicting contact objects:** The redemption process prevents sign-in issues when a guest user object conflicts with a contact object in the directory. Whenever you add or invite a guest with an email that matches an existing contact, the proxyAddresses property on the guest user object is left empty. Previously, External ID searched only the proxyAddresses property, so direct link redemption failed when it couldn't find a match. Now, External ID searches both the proxyAddresses and invited email properties.

## Redemption process through the invitation email

When you add a guest user to your directory by [using the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-add-guest-users-portal), an invitation email is sent to the guest. You can also choose to send invitation emails when you're [using PowerShell](https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-invite-powershell) to add guest users to your directory. Here's a description of the guest's experience when they redeem the link in the email.

1. The guest receives an [invitation email](https://learn.microsoft.com/en-us/entra/external-id/invitation-email-elements) that's from Microsoft Invitations on behalf of `<primary domain> <invites@<primary domain>.onmicrosoft.com>`.
2. The guest selects **Accept invitation** in the email.
3. The guest uses their own credentials to sign in to your directory. If the guest doesn't have an account that can be federated to your directory and the [email one-time passcode \(OTP\)](https://learn.microsoft.com/en-us/entra/external-id/one-time-passcode) feature isn't enabled, the guest is prompted to create a personal [Microsoft account \(MSA\)](https://support.microsoft.com/help/4026324/microsoft-account-how-to-create). Refer to the [invitation redemption flow](#invitation-redemption-flow) for details.
4. The guest is guided through the [consent experience](#consent-experience-for-the-guest) described in the Consent experience for the guest section.

## Invitation redemption flow

When a user selects the **Accept invitation** link in an [invitation email](https://learn.microsoft.com/en-us/entra/external-id/invitation-email-elements), Microsoft Entra ID automatically redeems the invitation based on the default redemption order:

[![Screenshot showing the redemption flow diagram.](https://learn.microsoft.com/en-us/entra/external-id/media/redemption-experience/invitation-redemption.png)](https://learn.microsoft.com/en-us/entra/external-id/media/redemption-experience/invitation-redemption.png#lightbox)

1. Microsoft Entra ID performs user-based discovery to determine if the user already exists in a managed Microsoft Entra tenant. \(Unmanaged Microsoft Entra accounts can't be used for the redemption flow.\) If the user’s user principal name \([UPN](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/plan-connect-userprincipalname#what-is-userprincipalname)\) matches both an existing Microsoft Entra account and a personal MSA, the user is prompted to choose which account they want to redeem with.
2. If an admin enables [SAML/WS-Fed IdP federation](https://learn.microsoft.com/en-us/entra/external-id/direct-federation), Microsoft Entra ID checks if the user’s domain suffix matches the domain of a configured SAML/WS-Fed identity provider and redirects the user to the preconfigured identity provider.

   Note

   Direct SAML/WS-Fed federation between two Microsoft Entra tenants is not a supported or recommended configuration. Even if a SAML trust is technically configured between two Entra tenants, Microsoft Entra still uses the native Entra-to-Entra [B2B collaboration](https://learn.microsoft.com/en-us/entra/external-id/direct-federation-overview) model and not SAML.
3. If an admin enables [Google federation](https://learn.microsoft.com/en-us/entra/external-id/google-federation), Microsoft Entra ID checks if the user’s domain suffix is gmail.com or googlemail.com and redirects the user to Google.
4. The redemption process checks if the user has an existing personal [MSA](https://learn.microsoft.com/en-us/entra/external-id/microsoft-account). If the user already has an existing MSA, they sign in with their existing MSA.
5. Once the user’s **home directory** is identified, the user is sent to the corresponding identity provider to sign in.
6. If no home directory is found and the email one-time passcode feature is *enabled* for guests, a [passcode is sent](https://learn.microsoft.com/en-us/entra/external-id/one-time-passcode#when-does-a-guest-user-get-a-one-time-passcode) to the user through the invited email. The user retrieves and enters this passcode in the Microsoft Entra sign-in page.
7. If no home directory is found and email one-time passcode for guests is *disabled*, the user is prompted to create a consumer MSA with the invited email. Microsoft Entra ID supports creating an MSA with work emails in domains that aren't verified in Microsoft Entra ID.
8. After authenticating to the right identity provider, the user is redirected to Microsoft Entra ID to complete the [consent experience](#consent-experience-for-the-guest).

## Configurable redemption

[Configurable redemption](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-overview) lets you customize the order of identity providers presented to guests when they redeem your invitations. When a guest selects the **Accept invitation** link, Microsoft Entra ID automatically redeems the invitation based on the [default order](#invitation-redemption-flow). Override this order by changing the identity provider redemption order in your [cross-tenant access settings](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-settings-b2b-collaboration).

## Consent experience for the guest

When a guest signs in to a resource in a partner organization for the first time, they see the following consent experience. The guest sees these consent pages only after sign-in, and they're not displayed at all if the user already accepted them.

1. The guest reviews the **Review permissions** page that describes the inviting organization's [privacy statement](https://learn.microsoft.com/en-us/entra/fundamentals/properties-area). To continue, the user must **Accept** the use of their information in accordance with the inviting organization's privacy policies.

   By agreeing to this consent prompt, you acknowledge that certain elements of your account are shared. These elements include your name, photo, and email address, as well as directory identifiers that the other organization might use to better manage your account and improve your cross-organization experience.

   ![Screenshot showing the Review permissions page.](https://learn.microsoft.com/en-us/entra/external-id/media/redemption-experience/new-review-permissions.png)

   Note

   For information about how you as a tenant administrator can link to your organization's privacy statement, see [How-to: Add your organization's privacy info in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/properties-area).
2. If terms of use are configured, the guest opens and reviews the terms of use, then selects **Accept**.

   ![Screenshot showing new terms of use.](https://learn.microsoft.com/en-us/entra/external-id/media/redemption-experience/terms-of-use-accept.png)

   You can configure [terms of use](https://learn.microsoft.com/en-us/entra/identity/conditional-access/terms-of-use) in **External Identities** > **Terms of use**.
3. Unless otherwise specified, the guest is redirected to the Apps access panel, which lists the applications the guest can access.

   [![Screenshot showing the Apps access panel.](https://learn.microsoft.com/en-us/entra/external-id/media/redemption-experience/myapps.png)](https://learn.microsoft.com/en-us/entra/external-id/media/redemption-experience/myapps.png#lightbox)

In your directory, the guest's **Invitation accepted** value changes to **Yes**. If an MSA was created, the guest’s **Source** shows **Microsoft Account**. For more information about guest user account properties, see [Properties of a Microsoft Entra B2B collaboration user](https://learn.microsoft.com/en-us/entra/external-id/user-properties). If you see an error that requires admin consent while accessing an application, see [how to grant admin consent to apps](https://learn.microsoft.com/en-us/entra/identity-platform/v2-admin-consent).

### Automatic redemption process setting

You might want to automatically redeem invitations so users don't have to accept the consent prompt when you add them to another tenant for B2B collaboration. When you configure this setting, the B2B collaboration user receives a notification email that requires no action from them. Users receive the notification email directly and don't need to access the tenant first before they get the email.

For information about how to automatically redeem invitations, see [cross-tenant access overview](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-overview#automatic-redemption-setting) and [Configure cross-tenant access settings for B2B collaboration](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-settings-b2b-collaboration).

## Additional information

- **Starting July 12, 2021**, if Microsoft Entra B2B customers set up new Google integrations for use with self-service sign-up for their custom or line-of-business applications, authentication with Google identities won't work until authentications are moved to system web-views. For details, see [Google web-view sign-in deprecation](https://learn.microsoft.com/en-us/entra/external-id/google-federation#deprecation-of-web-view-sign-in-support).
- **Starting September 30, 2021**, Google is [deprecating embedded web-view sign-in support](https://developers.googleblog.com/2016/08/modernizing-oauth-interactions-in-native-apps.html). If your apps authenticate users with an embedded web-view and you're using Google federation with [Azure AD B2C](https://learn.microsoft.com/en-us/azure/active-directory-b2c/identity-provider-google) or Microsoft Entra B2B for [external user invitations](https://learn.microsoft.com/en-us/entra/external-id/google-federation) or [self-service sign-up](https://learn.microsoft.com/en-us/entra/external-id/identity-providers), Google Gmail users won't be able to authenticate. For details, see [Google web-view sign-in deprecation](https://learn.microsoft.com/en-us/entra/external-id/google-federation#deprecation-of-web-view-sign-in-support).
- The [email one-time passcode feature](https://learn.microsoft.com/en-us/entra/external-id/one-time-passcode) is now turned on by default for all new tenants and for any existing tenants where you didn't explicitly turn it off. When this feature is turned off, the fallback authentication method is to prompt invitees to create a Microsoft account.

## Next steps

- [What is Microsoft Entra B2B collaboration?](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b)
- [B2B collaboration user properties](https://learn.microsoft.com/en-us/entra/external-id/user-properties)
- [Invitation email](https://learn.microsoft.com/en-us/entra/external-id/invitation-email-elements)
