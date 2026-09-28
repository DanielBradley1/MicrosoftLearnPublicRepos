<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-native-authentication-single-page-app-sdk-sign-in -->
<!-- Sitemap-Last-Modified: 2025-11-21 -->

# Quickstart: Sign in users in a single-page app by using native authentication JavaScript SDK

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

In this Quickstart, you use a single-page application \(SPA\) to demonstrate how to authenticate users by using native authentication SDK. The sample app demonstrates user sign-up, sign-in, and sign-out for both email with password and email one-time passcode authentication flows.

## Prerequisites

- An Azure account with an active subscription. If you don't already have one, [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- This Azure account must have permissions to manage applications. Any of the following Microsoft Entra roles include the required permissions:

  - Application Administrator
  - Application Developer

- An external tenant. If you don't have one, [create a new external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal) in the Microsoft Entra admin center.
- A user flow. For more information, see [create self-service sign-up user flows for apps in external tenants](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers). Under **Identity providers**, select your preferred method of authentication, that's, **Email with password** or **Email one-time passcode**. For this code sample, use the following user attributes in your user flow as the sample app collects them from the user:

  - **Given Name**
  - **Surname**
  - **Job Title**
  - **Country/Region**

- If you haven't already done so, [Register an application in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app). Make sure to:

  - Record the **Application \(client\) ID** and **Directory \(tenant\) ID** for later use.
  - [Grant admin consent](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app#grant-admin-consent-external-tenants-only) to the app registration.

- [Associate your app registration with the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application)
- [Node.js](https://nodejs.org/en/download/).
- [Visual Studio Code](https://code.visualstudio.com/download) or another code editor.

## Enable public client and native authentication flows

To specify that this app is a public client and can use native authentication, enable public client and native authentication flows:

1. From the app registrations page, select the app registration for which you want to enable public client and native authentication flows.
2. Under **Manage**, select **Authentication**.
3. Under **Advanced settings**, allow public client flows:

   1. For **Enable the following mobile and desktop flows** select **Yes**.
   2. For **Enable native authentication**, select **Yes**.

4. Select **Save** button.

## Clone or download sample SPA

To obtain the sample application, you can either clone it from GitHub or download it as a .zip file.

- To clone the sample, open a command prompt and navigate to where you wish to create the project, and enter the following command:

  ```console
  git clone https://github.com/Azure-Samples/ms-identity-ciam-native-javascript-samples.git
  ```

- [Download the sample](https://github.com/Azure-Samples/ms-identity-ciam-native-javascript-samples/archive/refs/heads/main.zip). Extract it to a file path where the length of the name is fewer than 260 characters.

## Install project dependencies

- [React](#tabpanel_1_react)
- [Angular](#tabpanel_1_angular)

1. Open a terminal window and navigate to the directory that contains the React sample app:

   ```console
       cd typescript/native-auth/react-nextjs-sample
   ```

2. Run the following command to install app dependencies:

   ```console
   npm install
   ```

1. Open a terminal window and navigate to the directory that contains the React sample app:

   ```console
       cd typescript/native-auth/angular-sample
   ```

2. Run the following command to install app dependencies:

   ```console
   npm install
   ```

## Configure the sample React app

- [React](#tabpanel_2_react)
- [Angular](#tabpanel_2_angular)

1. Open *src/config/auth-config.ts* and replace the following placeholders with the values obtained from the Microsoft Entra admin center:

   - Find the placeholder `Enter_the_Application_Id_Here` then replace it with the Application \(client\) ID of the app you registered earlier.
   - Find the placeholder `Enter_the_Tenant_Subdomain_Here` then replace it with the tenant subdomain in your Microsoft Entra admin center. For example, if your tenant primary domain is `contoso.onmicrosoft.com`, use `contoso`. If you don't have your tenant name, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal#get-the-external-tenant-details).

2. Save the changes.

1. Open *src/app/config/auth-config.ts* and replace the following placeholders with the values obtained from the Microsoft Entra admin center:

   - Find the placeholder `Enter_the_Application_Id_Here` then replace it with the Application \(client\) ID of the app you registered earlier.
   - Find the placeholder `Enter_the_Tenant_Subdomain_Here` then replace it with the tenant subdomain in your Microsoft Entra admin center. For example, if your tenant primary domain is `contoso.onmicrosoft.com`, use `contoso`. If you don't have your tenant name, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal).

2. Save the changes.

## Configure CORS proxy server

The native authentication API doesn't support [Cross-Origin Resource Sharing \(CORS\)](https://developer.mozilla.org/docs/Web/HTTP/CORS) so you must set up a proxy server between your SPA app and the APIs.

This code sample includes a CORS proxy server that forwards requests to native authentication API URL endpoints. The CORS proxy server is a Node.js server that listens on port 3001.

To configure the proxy server, open the *proxy.config.js* file, then the find the placeholder:

- `tenantSubdomain` and replace it with the Directory \(tenant\) subdomain. For example, if your tenant primary domain is `contoso.onmicrosoft.com`, use `contoso`. If you don't have your tenant subdomain, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal#get-the-external-tenant-details).
- `tenantId` and replace it with the Directory \(tenant\) ID. If you don't have your tenant ID, learn how to [read your tenant details](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal#get-the-external-tenant-details).

## Run and test your app

You've now configured the sample app and it's ready to run.

- [React](#tabpanel_3_react)
- [Angular](#tabpanel_3_angular)

1. From your terminal window, run the following commands to start the CORS proxy server:

   ```console
   cd typescript/native-auth/react-nextjs-sample/
   npm run cors
   ```

2. To start your React app, open another terminal window, then run the following commands:

   ```console
   cd typescript/native-auth/react-nextjs-sample/
   npm run dev
   ```

3. Open a web browser and go to `http://localhost:3000/`.
4. To sign up for an account, select **Sign Up**, then follow the prompts.
5. After you sign up, test sign-in and password reset by selecting **Sign In** and **Reset Password** buttorespectively.

1. From your terminal window, run the following commands to start the CORS proxy server:

   ```console
   cd typescript/native-auth/angular-sample/
   npm run cors
   ```

2. To start your React app, open another terminal window, then run the following commands:

   ```console
   cd typescript/native-auth/angular-sample/
   npm run start
   ```

3. Open a web browser and go to `http://localhost:4200`.
4. To sign up for an account, select **Sign Up**, then follow the prompts.
5. After you sign up, test sign-in and password reset by selecting **Sign In** and **Reset Password** buttorespectively.

## Enable sign-in with an alias or username

You can allow users who sign in with an email address and password to also sign in with a username and password. The username also called an alternate sign-in identifier, can be a customer ID, account number, or another identifier that you choose to use as a username.

You can assign usernames to the user account manually via the Microsoft Entra admin center or automate it in your app via the Microsoft Graph API.

Use the steps in [Sign in with an alias or username](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias) article to allow your users to sign-in using a username in your application:

1. [Enable username in sign-in](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#enable-username-in-sign-in-identifier-policy).
2. [Create users with username in the admin center](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#create-and-update-users-with-username) or [update existing users to by adding a username](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#create-and-update-users-with-username). Alternatively, you can also [automate user creation and updating in your app by using the Microsoft Graph API](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-alias#create-and-update-users-with-username).

## Related content

- [Build a React single-page app that uses native authentication SDK to authenticate users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-single-page-app-react-sdk-sign-up).
- [Build your Angular single-page app that uses native authentication SDK to authenticate users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-single-page-app-angular-sign-up).
