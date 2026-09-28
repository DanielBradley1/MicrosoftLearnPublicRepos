<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-native-authentication-macos-sign-in -->
<!-- Sitemap-Last-Modified: 2025-11-21 -->

# Sign in users in sample macOS app by using native authentication

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

This guide shows how to run an macOS sample application that demonstrates sign-up and sign in scenarios using Microsoft Entra External ID.

In this article, you learn how to:

- Enable public client and native authentication flows.
- Update a sample native macOS application to use your own external tenant details.
- Run and test the sample native macOS application.

## Prerequisites

- An Azure account with an active subscription. If you don't already have one, [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn)
- This Azure account must have permissions to manage applications. Any of the following Microsoft Entra roles include the required permissions:

  - Application Administrator
  - Application Developer

- An external tenant. If you don't have one, [create a new external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal) in the Microsoft Entra admin center.
- If you haven't already done so, [Register an application in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app). Make sure to:

  - Record the **Application \(client\) ID** and **Directory \(tenant\) ID** for later use.
  - [Grant admin consent](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app#grant-admin-consent-external-tenants-only) to the application.

- If you haven't already done so, [Create a user flow in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers)
- [Associate your app registration with the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application)
- [Xcode](https://developer.apple.com/xcode/resources/)

## Enable public client and native authentication flows

To specify that this app is a public client and can use native authentication, enable public client and native authentication flows:

1. From the app registrations page, select the app registration for which you want to enable public client and native authentication flows.
2. Under **Manage**, select **Authentication**.
3. Under **Advanced settings**, allow public client flows:

   1. For **Enable the following mobile and desktop flows** select **Yes**.
   2. For **Enable native authentication**, select **Yes**.

4. Select **Save** button.

## Clone sample macOS application

1. Open Terminal and navigate to a directory where you want to keep the code.
2. Clone the macOS application from GitHub by running the following command:

   ```bash
   git clone https://github.com/Azure-Samples/ms-identity-ciam-native-auth-macos-sample.git
   ```

3. Navigate to the directory where the repo was cloned:

   ```bash
   cd ms-identity-ciam-native-auth-macos-sample
   ```

## Configure the sample macOS application

1. In Xcode, open *NativeAuthSampleAppMacOS.xcodeproj* project.
2. Open *NativeAuthSampleAppMacOS/Configuration.swift* file.
3. Find the placeholder:

   - `Enter_the_Application_Id_Here` and replace it with the **Application \(client\) ID** of the app you registered earlier.
   - `Enter_the_Tenant_Subdomain_Here` and replace it with the Directory \(tenant\) subdomain. For example, if your tenant primary domain is `contoso.onmicrosoft.com`, use contoso. If you don't have your tenant subdomain, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal#get-the-external-tenant-details).

Note

Remember to select a scheme to build and destination where you run the built products. Each scheme contains a list of real or simulated devices that represent the available destinations.

## Run and test sample macOS application

To build and run your code, select **Run** from the **Product** menu in Xcode. After a successful build, Xcode will launch the sample app in the Simulator.

[![Screenshot of user prompt to enter email and password in macOS app.](https://learn.microsoft.com/en-us/entra/identity-platform/media/native-authentication/macos/native-auth-sign-in-sign-up-password-macos.png)](https://learn.microsoft.com/en-us/entra/identity-platform/media/native-authentication/macos/native-auth-sign-in-sign-up-password-expanded-macos.png#lightbox)

This guide tests **Email and password** usage. Enter a valid email address and password, select **Sign Up**, and launch the submit code screen:

[![Screenshot of user prompt to enter one-time passcode \(OTP\) in macOS app.](https://learn.microsoft.com/en-us/entra/identity-platform/media/native-authentication/macos/enter-one-time-pass-code-macos.png)](https://learn.microsoft.com/en-us/entra/identity-platform/media/native-authentication/macos/enter-one-time-pass-code-expanded-macos.png#lightbox)

After you enter your email address on the previous screen, the application will send a verification code to it. Once you submit the received code, the application takes you back to the previous screen and automatically signs you in.

## Enable sign-in with an alias or username

You can allow users who sign in with an email address and password to also sign in with a username and password. The username also called an alternate sign-in identifier, can be a customer ID, account number, or another identifier that you choose to use as a username.

You can assign usernames to the user account manually via the Microsoft Entra admin center or automate it in your app via the Microsoft Graph API.

Use the steps in [Sign in with an alias or username](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias) article to allow your users to sign-in using a username in your application:

1. [Enable username in sign-in](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#enable-username-in-sign-in-identifier-policy).
2. [Create users with username in the admin center](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#create-and-update-users-with-username) or [update existing users to by adding a username](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#create-and-update-users-with-username). Alternatively, you can also [automate user creation and updating in your app by using the Microsoft Graph API](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#create-and-update-users-with-username).

## Next steps

- [Tutorial: Prepare your iOS/macOS app for native authentication](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-native-authentication-prepare-ios-macos-app).
