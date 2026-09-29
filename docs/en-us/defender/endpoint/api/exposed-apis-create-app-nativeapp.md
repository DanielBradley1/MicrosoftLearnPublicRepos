<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-nativeapp -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Use Microsoft Defender for Endpoint APIs

Important

Advanced hunting capabilities are not included in Defender for Business.

Note

If you're a US Government customer, use the URIs listed in [Microsoft Defender for Endpoint for US Government customers](https://learn.microsoft.com/en-us/defender-endpoint/gov#api).

Tip

For better performance, instead of using api.security.microsoft.com, use a server closer to your geolocation:

- us.api.security.microsoft.com
- eu.api.security.microsoft.com
- uk.api.security.microsoft.com
- au.api.security.microsoft.com
- swa.api.security.microsoft.com
- ina.api.security.microsoft.com
- aea.api.security.microsoft.com

This page describes how to create an application to get programmatic access to Defender for Endpoint on behalf of a user.

If you need programmatic access Microsoft Defender for Endpoint without a user, refer to [Access Microsoft Defender for Endpoint with application context](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-webapp).

If you're not sure which access you need, read the [Introduction page](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

Microsoft Defender for Endpoint exposes much of its data and actions through a set of programmatic APIs. Those APIs enable you to automate work flows and innovate based on Microsoft Defender for Endpoint capabilities. The API access requires OAuth2.0 authentication. For more information, see [OAuth 2.0 Authorization Code Flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

In general, you need to take the following steps to use the APIs:

- Create a Microsoft Entra application
- Get an access token using this application
- Use the token to access Defender for Endpoint API

This page explains how to create a Microsoft Entra application, get an access token to Microsoft Defender for Endpoint and validate the token.

Note

When accessing Microsoft Defender for Endpoint API on behalf of a user, you will need the correct Application permission and user permission. If you are not familiar with user permissions on Microsoft Defender for Endpoint, see [Manage portal access using role-based access control](https://learn.microsoft.com/en-us/defender-endpoint/rbac).

Tip

If you have the permission to perform an action in the portal, you have the permission to perform the action in the API.

## Create an app

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Navigate to **Microsoft Entra ID** > **App registrations** > **New registration**.

   [![The App registrations page in the Microsoft Azure portal](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-azure-new-app2.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-azure-new-app2.png#lightbox)
3. When the **Register an application** page appears, enter your application's registration information:

   - **Name** - Enter a meaningful application name that is displayed to users of the app.
   - **Supported account types** - Select which accounts you would like your application to support.

       


     | Supported account types | Description |
     | --- | --- |
     | **Accounts in this organizational directory only** | Select this option if you're building a line-of-business \(LOB\) application. This option isn't available if you're not registering the application in a directory.  <br>  <br>This option maps to Microsoft Entra-only single-tenant.  <br>  <br>This option is the default option unless you're registering the app outside of a directory. In cases where the app is registered outside of a directory, the default is Microsoft Entra multitenant and personal Microsoft accounts. |
     | **Accounts in any organizational directory** | Select this option if you would like to target all business and educational customers.  <br>  <br>This option maps to a Microsoft Entra-only multitenant.  <br>  <br>If you registered the app as Microsoft Entra-only single-tenant, you can update it to be Microsoft Entra multitenant and back to single-tenant through the **Authentication** blade. |
     | **Accounts in any organizational directory and personal Microsoft accounts** | Select this option to target the widest set of customers.  <br>  <br>This option maps to Microsoft Entra multitenant and personal Microsoft accounts.  <br>  <br>If you registered the app as Microsoft Entra multitenant and personal Microsoft accounts, you can't change this in the UI. Instead, you must use the application manifest editor to change the supported account types. |

   - **Redirect URI \(optional\)** - Select the type of app you're building, **Web** or **Public client \(mobile & desktop\)**, and then enter the redirect URI \(or reply URL\) for your application.

     - For web applications, provide the base URL of your app. For example, `http://localhost:31544` might be the URL for a web app running on your local machine. Users would use this URL to sign in to a web client application.
     - For public client applications, provide the URI used by Microsoft Entra ID to return token responses. Enter a value specific to your application, such as `myapp://auth`.


     To see specific examples for web applications or native applications, check out our [quickstarts](https://learn.microsoft.com/en-us/azure/active-directory/develop/#quickstarts).


     When finished, select **Register**.

4. Allow your Application to access Microsoft Defender for Endpoint and assign it 'Read alerts' permission:

   - On your application page, select **API Permissions** > **Add permission** > **APIs my organization uses** > type **WindowsDefenderATP** and select on **WindowsDefenderATP**.

     Note

     *WindowsDefenderATP* does not appear in the original list. Start writing its name in the text box to see it appear.

     [![add permission.](https://learn.microsoft.com/en-us/defender-endpoint/media/add-permission.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/add-permission.png#lightbox)
   - Choose **Delegated permissions** > **Alert.Read** > select **Add permissions**.

     [![The application type and permissions panes](https://learn.microsoft.com/en-us/defender-endpoint/media/application-permissions-public-client.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/application-permissions-public-client.png#lightbox)


   Important


   Select the relevant permissions. Read alerts is only an example.


   For example:


   - To [run advanced queries](https://learn.microsoft.com/en-us/defender-endpoint/api/run-advanced-query-api), select **Run advanced queries** permission.
   - To [isolate a device](https://learn.microsoft.com/en-us/defender-endpoint/api/isolate-machine), select **Isolate machine** permission.
   - To determine which permission you need, view the **Permissions** section in the API you're interested to call.
   - Select **Grant consent**.

     Note

     Every time you add permission you must select on **Grant consent** for the new permission to take effect.

     [![The Grand admin consent option](https://learn.microsoft.com/en-us/defender-endpoint/media/grant-consent.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/grant-consent.png#lightbox)

5. Write down your application ID and your tenant ID.

   On your application page, go to **Overview** and copy the following information:

   [![The created app ID](https://learn.microsoft.com/en-us/defender-endpoint/media/app-and-tenant-ids.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/app-and-tenant-ids.png#lightbox)

## Get an access token

For more information on Microsoft Entra tokens, see [Microsoft Entra tutorial](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

Note

The example in this article uses interactive sign-in, which prompts the user to authenticate in a browser and supports multifactor authentication and Conditional Access. Avoid authentication flows that require the application to collect or handle a user's password directly. If you need programmatic access without a signed-in user, use [application context](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-webapp) with a managed identity or certificate credential instead.

### Using C#

Tip

Some Microsoft Defender for Endpoint APIs continue to require access tokens issued for the legacy resource `https://api.securitycenter.microsoft.com`. If the token audience doesn't match the resource expected by the API, requests fail with `403 Forbidden`, even if the API endpoint uses `https://api.security.microsoft.com`. Use `https://api.securitycenter.microsoft.com` as the resource or scope when acquiring tokens.

This example uses the [Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/msal/dotnet/) to acquire a token interactively. Before you run it:

- Add the [`Microsoft.Identity.Client`](https://www.nuget.org/packages/Microsoft.Identity.Client) NuGet package to your project.
- On your app registration, configure a **Mobile and desktop applications** platform with the `http://localhost` redirect URI, so the interactive flow can return the token.
- Copy/paste the following class into your application, then call **AcquireUserTokenAsync** with your application ID and tenant ID. The user is prompted to sign in interactively; their password is never handled by your application.

```csharp
    namespace WindowsDefenderATP
    {
        using System.Linq;
        using System.Threading.Tasks;
        using Microsoft.Identity.Client;

        public static class WindowsDefenderATPUtils
        {
            private const string Authority = "https://login.microsoftonline.com";

            // Microsoft Defender for Endpoint APIs expect tokens issued for this resource.
            private static readonly string[] Scopes = { "https://api.securitycenter.microsoft.com/.default" };

            public static async Task<string> AcquireUserTokenAsync(string appId, string tenantId)
            {
                // Public client application for a native (desktop) app.
                // No client secret or user password is stored or handled by the app.
                var app = PublicClientApplicationBuilder
                    .Create(appId)
                    .WithAuthority($"{Authority}/{tenantId}")
                    .WithDefaultRedirectUri() // http://localhost - register as a public client redirect URI
                    .Build();

                var account = (await app.GetAccountsAsync().ConfigureAwait(false)).FirstOrDefault();

                try
                {
                    // Reuse a cached token when one is available.
                    var silentResult = await app
                        .AcquireTokenSilent(Scopes, account)
                        .ExecuteAsync()
                        .ConfigureAwait(false);

                    return silentResult.AccessToken;
                }
                catch (MsalUiRequiredException)
                {
                    // First run or expired session: prompt the user to sign in.
                    // Uses the authorization code flow with PKCE and supports
                    // multifactor authentication and Conditional Access.
                    var interactiveResult = await app
                        .AcquireTokenInteractive(Scopes)
                        .ExecuteAsync()
                        .ConfigureAwait(false);

                    return interactiveResult.AccessToken;
                }
            }
        }
    }
```

Tip

For a headless or no-browser environment, use the [device code flow](https://learn.microsoft.com/en-us/entra/msal/dotnet/acquiring-tokens/desktop-mobile/device-code-flow) \(`AcquireTokenWithDeviceCode`\) instead of `AcquireTokenInteractive`.

## Validate the token

Verify to make sure you got a correct token:

- Copy/paste into [JWT](https://jwt.ms) the token you got in the previous step in order to decode it.
- Validate you get a 'scp' claim with the desired app permissions.
- In the screenshot below you can see a decoded token acquired from the app in the tutorial:

  [![The token validation page](https://learn.microsoft.com/en-us/defender-endpoint/media/nativeapp-decoded-token.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/nativeapp-decoded-token.png#lightbox)

## Use the token to access Microsoft Defender for Endpoint API

- Choose the API you want to use - [Supported Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-list).
- Set the Authorization header in the HTTP request you send to "Bearer {token}" \(Bearer is the Authorization scheme\).
- The Expiration time of the token is 1 hour \(you can send more than one request with the same token\).
- Example of sending a request to get a list of alerts **using C#**:

  ```csharp
  var httpClient = new HttpClient();

  var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/alerts");

  request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

  var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

  // Do something useful with the response
  ```

## See also

- [Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-list)
- [Access Microsoft Defender for Endpoint with application context](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-webapp)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
