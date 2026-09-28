<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-native-authentication-android-sign-in -->
<!-- Sitemap-Last-Modified: 2025-11-21 -->

# Sign in users in sample Android \(Kotlin\) app by using native authentication

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

In this quickstart you learn how to run an Android sample application that demonstrates sign-up, sign in, sign out, and password reset scenarios using Microsoft Entra's [native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication).

## Prerequisites

- An Azure account with an active subscription. If you don't already have one, [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- This Azure account must have permissions to manage applications. Any of the following Microsoft Entra roles include the required permissions:

  - Application Administrator
  - Application Developer

- An external tenant. If you don't have one, [create a new external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal) in the Microsoft Entra admin center.
- If you haven't already done so, [Register an application in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app). Make sure to:

  - Record the **Application \(client\) ID** and **Directory \(tenant\) ID** for later use.
  - [Grant admin consent](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app#grant-admin-consent-external-tenants-only) to the application.

- If you haven't already done so, [Create a user flow in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers)
- [Associate your app registration with the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application)
- [Android Studio](https://developer.android.com/studio).

## Enable public client and native authentication flows

To specify that this app is a public client and can use native authentication, enable public client and native authentication flows:

1. From the app registrations page, select the app registration for which you want to enable public client and native authentication flows.
2. Under **Manage**, select **Authentication**.
3. Under **Advanced settings**, allow public client flows:

   1. For **Enable the following mobile and desktop flows** select **Yes**.
   2. For **Enable native authentication**, select **Yes**.

4. Select **Save** button.

## Clone sample Android mobile application

1. Open Terminal and navigate to a directory where you want to keep the code.
2. Clone the application from GitHub by running the following command:

   ```bash
   git clone https://github.com/Azure-Samples/ms-identity-ciam-native-auth-android-sample 
   ```

## Configure the sample Android mobile application

1. In Android Studio, open the project that you cloned.
2. Open *app/src/main/res/raw/native\_auth\_sample\_app\_config.json* file.
3. Find the placeholder:

   - `Enter_the_Application_Id_Here` and replace it with the **Application \(client\) ID** of the app you registered earlier.
   - `Enter_the_Tenant_Subdomain_Here` and replace it with the Directory \(tenant\) subdomain. For example, if your tenant primary domain is `contoso.onmicrosoft.com`, use `contoso`. If you don't know your tenant subdomain, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal#get-the-external-tenant-details).

You've now configured the app and it's ready to run.

## Run and test the sample Android mobile application

To build and run your app, follow these steps:

1. In the toolbar, select your app from the run configurations menu.
2. In the target device menu, select the device that you want to run your app on.

   If you don't have any devices configured, you need to either create an Android Virtual Device to use the Android Emulator or connect a physical Android device.
3. Select the **Run** button. The app opens the **Email & OTP** screen.

   [![Screenshot of user prompt to enter email in Android application.](https://learn.microsoft.com/en-us/entra/identity-platform/media/native-authentication/android/android-email-otp.png)](https://learn.microsoft.com/en-us/entra/identity-platform/media/native-authentication/android/android-email-otp-expanded.png#lightbox)
4. Enter a valid email address and select then **Sign up** button. The app opens the submit code screen and you receive an OTP code in the email address.

   [![Screenshot of user prompt to enter one-time passcode in Android application.](https://learn.microsoft.com/en-us/entra/identity-platform/media/native-authentication/android/android-submit-code.png)](https://learn.microsoft.com/en-us/entra/identity-platform/media/native-authentication/android/android-submit-code-expanded.png#lightbox)
5. Enter the OTP code that you receive in the email inbox and select **Next**. If the sign-up is successful, the app signs you in automatically. If you don't receive the OTP code in your email inbox, you can resend it after a while by selecting **Resend Passcode**.
6. To sign out, select the **Sign out** button.

### Other scenarios that this sample supports

This sample app also supports the following authentication flows:

- **Email + password** covers sign-in or sign-up flows with an email with password.
- **Email + password sign-up with user attributes** covers sign-up with email and password, and submitting user attributes.
- **Password reset** covers self-service password reset \(SSPR\).
- **Access Protected API** covers call a protected API after the user successfully signs up or signs in and acquires an access token.
- **Fallback to web browser** covers the use the browser-based authentication as a fallback mechanism when the user can't complete authentication through native authentication for whatever reason.

## Test email with password flow

In this section, you test email with password flow, with its variants such as, email with password sign-up with user attributes and SSPR:

1. Use the steps in [create a user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers) to create a new user flow, but this time select **Email with password** as your authentication method. You need to configure **Country/Region** and **City** as the user attributes. Alternatively, you can modify the existing user flow to use **Email with password** \(Select **External Identities** > **User flows** > **SignInSignUpSample** > **Identity providers** > **Email with password** > **Save**\).
2. Use the steps in [associate the application with the new user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application) to add an app to your new user flow.
3. Run the sample app, then select the ellipsis menu \(**...**\) to open more options.
4. Select the scenario you want to test, such as **Email + password** or **Email + password sign-up with user attributes** or **Password reset**, then follow the prompts. To test **Password reset**, you need to first sign up a user, and [enable email one-time passcode](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-enable-password-reset-customers) for all users in your tenant.

## Test call a protected API flow

Use the steps in [Call a protected web API in a sample Android mobile app by using native authentication](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-native-authentication-android-call-api) to call a protected web API from a sample Android mobile app.

## Enable sign-in with an alias or username

You can allow users who sign in with an email address and password to also sign in with a username and password. The username also called an alternate sign-in identifier, can be a customer ID, account number, or another identifier that you choose to use as a username.

You can assign usernames to the user account manually via the Microsoft Entra admin center or automate it in your app via the Microsoft Graph API.

Use the steps in [Sign in with an alias or username](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias) article to allow your users to sign-in using a username in your application:

1. [Enable username in sign-in](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#enable-username-in-sign-in-identifier-policy).
2. [Create users with username in the admin center](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#create-and-update-users-with-username) or [update existing users to by adding a username](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#create-and-update-users-with-username). Alternatively, you can also [automate user creation and updating in your app by using the Microsoft Graph API](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#create-and-update-users-with-username).

## Next steps

[Tutorial: Prepare your Android app for native authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-native-authentication-prepare-android-app).
