<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-dotnet-call-api -->
<!-- Sitemap-Last-Modified: 2025-03-12 -->

# Tutorial: Test an ASP.NET Core web app that signs in users

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

In this tutorial, you test the sign in and sign out experience of your ASP.NET Core web app and view the claims in the ID token. In the [previous tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-dotnet-sign-in-users), you added the authentication elements, the sign-in, and sign-out experiences to the application to enable your app call a web API. For the purposes of this tutorial, the Microsoft Graph API is called to display the profile information of the logged-in user.

In this tutorial, you:

- Test the application and display ID token claims
- Sign out of the application
- Clean up resources

## Prerequisites

- Completion of the prerequisites and steps in [Tutorial: Add sign in to an application](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-dotnet-sign-in-users).

## Test the application

This section demonstrates how to test the application by signing in and calling the Microsoft Graph API to display the profile information of the logged-in user.

- [Workforce tenant](#tabpanel_1_workforce-tenant)
- [External tenant](#tabpanel_1_external-tenant)

1. Start the application by typing the following in the terminal, which launches the `https` profile in the *launchSettings.json* file.

   ```bash
   dotnet run --launch-profile https
   ```

2. Open a new private browser, and enter the application URI into the browser, in this case `https://localhost:5001`.
3. After the sign-in window appears, select the account in which to sign in with. Ensure the account matches the criteria of the app registration.
4. Fill in your email, one time-passcode as instructed to complete the sign-in flow. You can choose to stay signed in or not in the **Stay signed in** window.
5. The application requests permission to maintain access to data you have given it access to, and to sign you in and read your profile. Select **Accept**.
6. The following screenshot appears, indicating that you've signed in to the application. The ID token claims are displayed automatically.

   [![Screenshot depicting the results of the API call.](https://learn.microsoft.com/en-us/entra/identity-platform/media/tutorial-web-app-dotnet-sign-in-sign-in-out/display-aspnet-welcome.png)](https://learn.microsoft.com/en-us/entra/identity-platform/media/tutorial-web-app-dotnet-sign-in-sign-in-out/display-aspnet-welcome.png#lightbox)

1. Start the application by typing the following in the terminal, which launches the `https` profile in the *launchSettings.json* file.

   ```bash
   dotnet run --launch-profile https
   ```

2. Open a new private browser, and enter the application URI into the browser, in this case `https://localhost:5001`.
3. To test the sign-up user flow you configured earlier, select **No account? Create one**.
4. In the **Create account** window, enter the email address registered to your external tenant, which starts the sign-up flow as a user for your application.
5. Fill in your email, one time-passcode, new password as instructed to complete the sign-up flow. You can choose to stay signed in or not in the **Stay signed in** window.
6. The application requests permission to maintain access to data it you have given it access to, and to sign you in and read your profile. Select **Accept**.
7. The following screenshot appears, indicating that you've signed in to the application. The ID token claims are displayed automatically.

   [![Screenshot depicting the results of the API call.](https://learn.microsoft.com/en-us/entra/identity-platform/media/tutorial-web-app-dotnet-sign-in-sign-in-out/display-aspnet-welcome.png)](https://learn.microsoft.com/en-us/entra/identity-platform/media/tutorial-web-app-dotnet-sign-in-sign-in-out/display-aspnet-welcome.png#lightbox)

## Sign out from the application

Now that the application is tested and called the Microsoft Graph API, you should sign out of the application.

1. Find the **Sign out** link in the top right corner of the page, and select it.
2. You're prompted to pick an account to sign out from. Select the account you used to sign in.
3. A message appears indicating that you signed out. You can now close the browser window.

## Clean up resources

You should delete the application registration if you don't plan on using it further. You can also delete your local application and self signed certificate.

1. Navigate to your application's **Overview** page in the Microsoft Entra admin center, and select **Delete** at the top of the page. Check the box in the side panel and select **Delete**.
2. Find your local application and delete it using either your IDE or the terminal.
3. Check that your certificate isn't being used by another test application, then repeat the process with your self-signed certificate.

## See also

- [Enable self-service password reset](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-enable-password-reset-customers)
