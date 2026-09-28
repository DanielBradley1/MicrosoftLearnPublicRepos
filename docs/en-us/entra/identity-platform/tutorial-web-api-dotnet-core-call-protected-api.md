<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-api-dotnet-core-call-protected-api -->
<!-- Sitemap-Last-Modified: 2025-04-04 -->

# Test a protected ASP.NET Core web API

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

This tutorial is the final part of a series that demonstrates building and testing a protected web API registered in a Microsoft Entra tenant. In [Part 1 of this series](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-api-dotnet-core-build-app), you created an ASP.NET Core web API and protected its endpoints. You'll now create a lightweight daemon app, register it in your tenant, and use the daemon app to test the web API you built.

In this tutorial, you:

- Register a daemon app
- Assign an app role to your daemon app
- Build your daemon app
- Run your daemon app to call the protected web API

## Prerequisites

- If you haven't already, complete the [Tutorial: Build and protect an ASP.NET Core web API with the Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-api-dotnet-core-build-app)

## Register the daemon app

The following steps show you how to register your daemon app in the Microsoft Entra admin center:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Application Developer](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-developer).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/external-id/customers/media/common/admin-center-settings-icon.png) in the top menu to switch to your external tenant from the **Directories + subscriptions** menu.
3. Browse to **Entra ID** > **App registrations**.
4. Select **+ New registration**.
5. In the **Register an application page** that appears, enter your application's registration information:

   1. In the **Name** section, enter a meaningful application name that will be displayed to users of the app, for example *ciam-client-app*.
   2. Under **Supported account types**, select **Accounts in this organizational directory only**.

6. Select **Register**.
7. The application's **Overview pane** is displayed when registration is complete. Record the **Directory \(tenant\) ID** and the **Application \(client\) ID** to be used in your application source code.

Create a client secret for the registered application. The application uses the client secret to prove its identity when it requests for tokens:

1. From the **App registrations** page, select the application that you created \(such as *web app client secret*\) to open its **Overview** page.
2. Under **Manage**, select **Certificates & secrets** > **Client secrets** > **New client secret**.
3. In the **Description** box, enter a description for the client secret \(for example, *web app client secret*\).
4. Under **Expires**, select a duration for which the secret is valid \(per your organizations security rules\), and then select **Add**.
5. Record the secret's **Value**. You use this value for configuration in a later step. The secret value won't be displayed again, and isn't retrievable by any means, after you navigate away from the **Certificates and secrets**. Make sure you record it.

## Assign an app role to your daemon app

Applications that authenticate by themselves without a user require app permissions \(also known as roles\). These permissions allow the app itself to access resources directly. On the other hand, if we were testing the API with a signed-in user, we would assign delegated permissions \(scopes\). Delegated permissions enable the app to act on behalf of the user, limited to the user’s access rights. Follow these steps to assign application permissions to the daemon app:

1. From the **App registrations** page, select the application that you created, such as *ciam-client-app*.
2. Under **Manage**, select **API permissions**.
3. Under **Configured permissions**, select **Add a permission**.
4. Select the **APIs my organization uses** tab.
5. In the list of APIs, select the API such as *ciam-ToDoList-api*.
6. Select **Application permissions** option. We select this option as the app signs in as itself, but not on behalf of a user.
7. From the permissions list, select **TodoList.Read.All, ToDoList.ReadWrite.All** \(use the search box if necessary\).
8. Select the **Add permissions** button.
9. At this point, you've assigned the permissions correctly. However, since the daemon app doesn't allow users to interact with it, the users themselves can't consent to these permissions. To address this problem, you as the admin must consent to these permissions on behalf of all the users in the tenant:

   1. Select **Grant admin consent for <your tenant name>**, then select **Yes**.
   2. Select **Refresh**, then verify that **Granted for <your tenant name>** appears under **Status** for both permissions.

## Build a daemon app

1. Initialize a .NET console app and navigate to its root folder:

   ```dotnetcli
   dotnet new console -o MyTestApp
   cd MyTestApp
   ```

2. Install MSAL.NET to help with handling authentication by running the following command:

   ```dotnetcli
   dotnet add package Microsoft.Identity.Client
   ```

3. Run your API project and note the port on which it's running.
4. Open the *Program.cs* file and replace the "Hello world" code with the following code.

   ```csharp
   using System;
   using System.Net.Http;
   using System.Net.Http.Headers;

   HttpClient client = new HttpClient();

   var response = await client.GetAsync("http://localhost:<your-api-port>/api/todolist");
   Console.WriteLine("Your response is: " + response.StatusCode);
   ```


   Navigate to the daemon app root directory and run app using the command `dotnet run`. This code sends a request without an access token. You should see the string: *Your response is: Unauthorized* printed in your console.

5. Remove the code in step 4 and replace with the following to test your API by sending a request with a valid access token. This daemon app uses the client credentials flow to acquire an access token as it authenticates without user interaction.

   ```csharp
   using Microsoft.Identity.Client;
   using System;
   using System.Net.Http;
   using System.Net.Http.Headers;

   HttpClient client = new HttpClient();

   var clientId = "<your-daemon-app-client-id>";
   var clientSecret = "<your-daemon-app-secret>";
   var scopes = new[] {"api://<your-web-api-application-id>/.default"};
   var tenantId = "<your-tenant-id>";     //Use in workforce tenant configuration
   var tenantName = "<your-tenant-name>"; //Use in external tenant configuration
   var authority = $"https://login.microsoftonline.com/{tenantId}"; // Use "https://{tenantName}.ciamlogin.com" for external tenant configuration 

   var app = ConfidentialClientApplicationBuilder
       .Create(clientId)
       .WithAuthority(authority)
       .WithClientSecret(clientSecret)
       .Build();

   var result = await app.AcquireTokenForClient(new string[] { scopes }).ExecuteAsync();
   Console.WriteLine($"Access Token: {result.AccessToken}");

   client.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", result.AccessToken);
   var response = await client.GetAsync("http://localhost:/<your-api-port>/api/todolist");
   var content = await response.Content.ReadAsStringAsync();

   Console.WriteLine("Your response is: " + response.StatusCode);
   Console.WriteLine(content);
   ```

6. Replace the placeholders in the code with your daemon app client ID, secret, web API application ID, and tenant name.

   - For external tenants, use authority in the form: `"https://{tenantName}.ciamlogin.com/"`
   - For workforce tenants, use authority in the form: `"https://login.microsoftonline.com/{tenantId}"`

7. Navigate to the daemon app root directory and run app using the command `dotnet run`. This code sends a request with a valid access token. You should see the string: *Your response is: OK* printed in your console.

## Related content

- [How to call a protected Web API with cURL](https://learn.microsoft.com/en-us/entra/identity-platform/howto-call-a-web-api-with-curl)
- [How to call a protected web API with Insomnia](https://learn.microsoft.com/en-us/entra/identity-platform/howto-call-a-web-api-with-rest-client)
