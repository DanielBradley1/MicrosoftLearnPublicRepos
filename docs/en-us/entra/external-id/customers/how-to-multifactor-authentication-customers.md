<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-multifactor-authentication-customers -->
<!-- Sitemap-Last-Modified: 2026-05-28 -->

# Add multifactor authentication \(MFA\) to an app

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Multifactor authentication \(MFA\) adds a layer of security to your applications by requiring users to provide a second method for verifying their identity during sign-up or sign-in. External tenants support the following methods for authentication as a second factor:

- **Email one-time passcode**: After the user signs in with their email and password, they are prompted for a passcode that is sent to their email. To allow the use of email one-time passcodes for MFA, set your local account authentication method to *Email with password*. If you choose *Email with one-time passcode*, customers who use this method for primary sign-in won't be able to use it for MFA secondary verification.
- **SMS-based authentication**: While SMS isn't an option for first factor authentication, it's available as a second factor for MFA. Users who sign in with email and password, email and one-time passcode, or social identities like Google, Facebook or Apple, are prompted for second verification using SMS. Our SMS MFA includes automatic fraud checks. If we suspect fraud, we'll ask the user to complete a CAPTCHA to confirm they're not a robot before sending the SMS code for verification. It also provides safeguards against [telephony fraud](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-region-code-opt-in). SMS is an add-on feature. Your tenant must be [linked](https://learn.microsoft.com/en-us/entra/external-id/external-identities-pricing#link-an-external-tenant-to-a-subscription) to an active, valid subscription. [Learn more](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-multifactor-authentication-customers#sms-based-authentication)
- **Passkey \(FIDO2\)**: Passkeys provide phishing-resistant, passwordless authentication that satisfies MFA in a single gesture \(face, fingerprint, PIN, or security key\). Users can also use a passkey as a primary, passwordless sign-in method. For setup, see [Sign in with passkeys](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-with-passkey).

This article describes how to enforce MFA for your customers by creating a Microsoft Entra Conditional Access policy and adding MFA to your sign-up and sign-in user flow.

## Prerequisites

- A Microsoft Entra external tenant.
- A [sign-up and sign-in user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers).
- An app that's registered in your external tenant and added to the sign-up and sign-in user flow.
- An account with at least the Security Administrator role to configure Conditional Access policies and MFA.
- SMS is an add-on feature and requires a [linked subscription](https://learn.microsoft.com/en-us/entra/external-id/external-identities-pricing#link-an-external-tenant-to-a-subscription). If your subscription expires or is canceled, end users will no longer be able to authenticate using SMS, which could block them from signing in depending on your MFA policy.

## Create a Conditional Access policy

Create a Conditional Access policy in your external tenant that prompts users for MFA when they sign up or sign in to your app. \(For more information, see [Common Conditional Access policy: Require MFA for all users](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-mfa-strength)\).

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu to switch to your external tenant from the **Directories + subscriptions** menu.
3. Browse to **Entra ID** > **Conditional Access** > **Policies**, and then select **New policy**.

   [![Screenshot of the new policy button.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/new-policy.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/new-policy.png#lightbox)
4. Give your policy a name. We recommend that organizations create a meaningful standard for the names of their policies.
5. Under **Assignments**, select the link under **Users**.

   a. On the **Include** tab, select **All users**.

   b. On the **Exclude** tab, select **Users and groups** and choose your organization's emergency access or break-glass accounts. Then choose **Select**.

   [![Screenshot of assigning users to the new policy.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/new-policy-users.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/new-policy-users.png#lightbox)
6. Select the link under **Target resources**.

   a. On the **Include** tab, choose one of the following options:

   - Choose **All resources \(formerly 'All cloud apps'\)**.
   - Choose **Select resources** and select the link under **Select**. Find your app, select it, and then choose **Select**.


   b. On the **Exclude** tab, select any applications that don't require multifactor authentication.


   [![Screenshot of assigning apps to the new policy.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/new-policy-apps.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/new-policy-apps.png#lightbox)

7. Under **Access controls** select the link under **Grant**. Select **Grant access**, select **Require multifactor authentication**, and then choose **Select**.

   [![Screenshot of requiring MFA.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/new-policy-grant-require-mfa.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/new-policy-grant-require-mfa.png#lightbox)
8. Confirm your settings and set **Enable policy** to **On**.
9. Select **Create** to create to enable your policy.

## Enable email one-time passcode as an MFA method

Enable the email one-time passcode authentication method in your external tenant for all users.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator).
2. Browse to **Entra ID** > **Authentication methods**.
3. In the **Method** list, select **Email OTP**.

   [![Screenshot of the email one-time passcode option.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/auth-methods-eotp.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/auth-methods-eotp.png#lightbox)
4. Under **Enable and Target**, turn the **Enable** toggle on.
5. Under **Include**, next to **Target**, select **All users**.

   [![Screenshot of enabling email one-time passcode.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/enable-eotp.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/enable-eotp.png#lightbox)
6. Select **Save**.

## Enable SMS as an MFA method

Enable the SMS authentication method in your external tenant for all users.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator).
2. Browse to **Entra ID** > **Authentication methods**.
3. In the **Method** list, select **SMS**.

   [![Screenshot of the SMS option.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/auth-methods-sms.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/auth-methods-sms.png#lightbox)
4. Under **Enable and Target**, turn the **Enable** toggle on.
5. Under **Include**, next to **Target**, select **All users**.

   [![Screenshot of enabling SMS.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/enable-sms.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-multifactor-authentication-customers/enable-sms.png#lightbox)
6. Select **Save**.

### Activate telecom for opt-in regions

Starting January 2025, certain country codes will be deactivated by default for SMS verification. If you want to allow traffic from deactivated regions, you need to activate them for your application using the Microsoft Graph `onPhoneMethodLoadStartevent` policy. See [Regions requiring opt-in for SMS verification](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-region-code-opt-in).

## Test the sign-in

In a private browser, open your application and select **Sign-in**. You should be prompted for another authentication method.
