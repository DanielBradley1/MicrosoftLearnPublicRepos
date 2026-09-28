<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-enable-password-reset-customers -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# Enable self-service password reset

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Self-service password reset \(SSPR\) in Microsoft Entra External ID gives customers the ability to change or reset their password, with no administrator or help desk involvement. If a customer's account is locked or they forget their password, they can follow prompts to unblock themselves and get back to work.

## How the password reset process works

Self-service password reset \(SSPR\) supports two authentication methods: email one-time passcode \(Email OTP\) and SMS. When SSPR is enabled, users who forget their password can verify their identity using either Email OTP or SMS. With one-time passcode authentication, a passcode is sent by email or SMS. After entering the passcode, the user is prompted to create a new password.

The process works as follows:

1. From the app, the user selects **Sign in**.
2. On the sign-in page, they enter their email address and choose **Next**.
3. If the user forgot their password, they select **Forgot password?**.
4. The user is prompted to choose how to verify their identity. They can select a one-time passcode sent to their email or phone, based on the methods they registered.
5. A one-time passcode is sent to the email address they entered on the first page or to their registered phone number.
6. The user enters the passcode to continue.
7. After successfully verifying their identity, the user is prompted to create a new password.

## Prerequisites

- If you haven't already created your own external tenant, create one now.
- Have at least the [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator) role.
- If you haven't already created a User flow, [create one](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers) now.

## Enable self-service password reset for customers

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu to switch to the external tenant you created earlier from the **Directories + subscriptions** menu.
3. Browse to **Entra ID** > **External Identities** > **User flows**.
4. From the list of **User flows**, select the user flow you want to enable SSPR.
5. Make sure that the sign-up user flow registers **Email with password** as an authentication method under **Identity providers**.

   ![Screenshot that shows how to enable email authentication.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-enable-password-reset-customers/email-authentication-method.png)

### Enable authentication method for password reset

To enable self-service password reset, configure the authentication method for all users or for a specific group in your tenant. Choose one of the following tabs to see the steps for each method.

- [Email OTP](#tabpanel_1_emailotp)
- [SMS](#tabpanel_1_sms)

The following steps show how to enable **Email OTP** as an authentication method for self-service password reset.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com). If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu and switch to your external tenant from the **Directories + subscriptions** menu.
2. Browse to **Entra ID** > **Authentication methods**.
3. Under **Policies** > **Method** select **Email OTP**.

   ![Screenshot that shows authentication methods.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-enable-password-reset-customers/authentication-methods.png)
4. Under **Enable and Target**, turn on Email OTP.
5. Under **Include**, choose **All users** or **Select groups** to specify who can use this method.

   ![Screenshot of enabling OTP.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-enable-password-reset-customers/enable-otp.png)
6. Select **Save**.

To use SMS for self-service password reset, users need to register their phone number as a multifactor authentication \(MFA\) method. There are two ways to do this:

- MFA registration happens automatically when an admin sets up a Conditional Access policy that requires [MFA](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-mfa-strength).
- Admins can manually add their phone number under [Authentication methods](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-mfa-userdevicesettings#add-or-change-authentication-methods-for-a-user).

The following steps show how to enable **SMS** as an authentication method for self-service password reset.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com). If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu and switch to your external tenant from the **Directories + subscriptions** menu.
2. Browse to **Entra ID** > **Authentication methods**.
3. Under **Policies** > **Method** select **SMS**.

   ![Screenshot that shows authentication methods including SMS.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-enable-password-reset-customers/authentication-methods-sms.png)
4. Under **Enable and Target**, turn on SMS.
5. Under **Include**, choose **All users** or **Select groups** to specify who can use this method.

   ![Screenshot of enabling SMS.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-enable-password-reset-customers/enable-sms.png)

Note

Self-service password reset with Phone SMS includes built-in integration with the Phone Reputation platform to detect telephony fraud in real time. Each request returns an *Allow*, *Block*, or *Challenge* decision to help protect users. SMS-based password reset is part of an add-on feature with [tiered pricing](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-multifactor-authentication-customers#sms-pricing-tiers-by-countryregion) based on location or region. Charges per SMS include fraud protection services.

6. Select **I Acknowledge** to accept the SMS terms of use.
7. Select **Save**.

### Enable the password reset link \(optional\)

You can hide, show, or customize the self-service password reset link on the sign-in page.

1. In the search bar, type and select **Company Branding**.
2. Under **Default sign-in** select **Edit**.
3. On the **Sign-in form** tab, scroll to the **Self-service password reset** section and select **Show self-service password reset**.

   ![Screenshot of the company branding Self-service password reset.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-customize-branding-customers/company-branding-self-service-password-reset.png)
4. Select **Review + save** and **Save** on the **Review** tab.

For more details, check out the [Customize the neutral branding in your external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers#to-customize-self-service-password-reset) article.

## Test self-service password reset

To go through the self-service password reset flow:

1. Open your application, and select **Sign-in**.
2. In the sign-in page, enter your **Email address** and select **Next**.

   ![Screenshot that shows the sign-in page.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-enable-password-reset-customers/sign-in.png)
3. Select the **Forgot password?** link.

   ![Screenshot that shows the forgot password link.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-enable-password-reset-customers/forgot-password.png)
4. If SMS is available for self-service password reset, you can choose to receive a one-time passcode by email or phone. Enter the passcode sent to your email address or phone number.
5. Once you're authenticated, you're prompted to enter a new password. Provide a **New password**, and **Confirm password**, then select **Reset password** to sign in to your application.

   ![Screenshot that shows the update password screen.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-enable-password-reset-customers/update-password.png)

## Related content

- Add [Google](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-google-federation-customers), [Facebook](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-facebook-federation-customers), [Apple](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-apple-federation-customers), or a custom [OIDC federation](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-oidc-federation-customers) federation.
