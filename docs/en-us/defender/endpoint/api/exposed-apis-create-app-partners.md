<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-partners -->
<!-- Sitemap-Last-Modified: 2026-02-17 -->

# Partner access through Microsoft Defender for Endpoint APIs

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

This page describes how to create a Microsoft Entra application to get programmatic access to Microsoft Defender for Endpoint on behalf of your customers.

Microsoft Defender for Endpoint exposes much of its data and actions through a set of programmatic APIs. Those APIs help you automate work flows and innovate based on Microsoft Defender for Endpoint capabilities. The API access requires OAuth2.0 authentication. For more information, see [OAuth 2.0 Authorization Code Flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

In general, you need to take the following steps to use the APIs:

1. Create a multi-tenant Microsoft Entra application.
2. Get authorized\(consent\) by your customer administrator for your application to access Defender for Endpoint resources it needs.
3. Get an access token using this application.
4. Use the token to access Microsoft Defender for Endpoint API.

The following steps guide you how to create a Microsoft Entra application, get an access token to Microsoft Defender for Endpoint and validate the token.

Important

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

## Create the multitenant app

1. Sign in to your [Azure tenant](https://portal.azure.com).
2. Navigate to **Microsoft Entra ID** > **App registrations** > **New registration**.

   [![The navigation to application registration pane](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-azure-new-app2.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-azure-new-app2.png#lightbox)
3. In the registration form:

   - Choose a name for your application.
   - Supported account types - accounts in any organizational directory.
   - Redirect URI - type: Web, URI: [https://portal.azure.com](https://portal.azure.com)

     [![The Microsoft Azure partner application registration page](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-api-new-app-partner.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-api-new-app-partner.png#lightbox)

4. Allow your Application to access Microsoft Defender for Endpoint and assign it with the minimal set of permissions required to complete the integration.

   - On your application page, select **API Permissions** > **Add permission** > **APIs my organization uses** > type **WindowsDefenderATP** and select on **WindowsDefenderATP**.
   - `WindowsDefenderATP` doesn't appear in the original list. Start writing its name in the text box to see it appear.

     [![The Add a permission option](https://learn.microsoft.com/en-us/defender-endpoint/media/add-permission.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/add-permission.png#lightbox)

### Request API permissions

To determine which permission you need, review the **Permissions** section in the API you want to call. For instance:

- To [run advanced queries](https://learn.microsoft.com/en-us/defender-endpoint/api/run-advanced-query-api), select the **Run advanced queries** permission.
- To [isolate a device](https://learn.microsoft.com/en-us/defender-endpoint/api/isolate-machine), select the **Isolate machine** permission.

In the following example we use **Read all alerts** permission:

1. Choose **Application permissions** > **Alert.Read.All** > select on **Add permissions**

   [![The option that allows to add a permission](https://learn.microsoft.com/en-us/defender-endpoint/media/application-permissions.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/application-permissions.png#lightbox)
2. Select **Grant consent**

   - Every time you add permission you must select on **Grant consent** for the new permission to take effect.


   [![The option that allows consent to be granted](https://learn.microsoft.com/en-us/defender-endpoint/media/grant-consent.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/grant-consent.png#lightbox)

3. Add a secret to the application.

   - Select **Certificates & secrets**, add description to the secret and select **Add**.


   After you select **Add**, make sure to copy the generated secret value. You won't be able to retrieve it after you leave!


   [![The create app key](https://learn.microsoft.com/en-us/defender-endpoint/media/webapp-create-key2.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/webapp-create-key2.png#lightbox)

4. Write down your application ID:

   - On your application page, go to **Overview** and copy the following information:

     [![The create application's ID](https://learn.microsoft.com/en-us/defender-endpoint/media/app-id.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/app-id.png#lightbox)

5. Add the application to your customer's tenant.

   You need your application to be approved in each customer tenant where you intend to use it. This approval is necessary because your application interacts with Microsoft Defender for Endpoint application on behalf of your customer.

   A user account with appropriate permissions for your customer's tenant must select the consent link and approve your application.

   The consent link is of the form:

   ```http
   https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=00000000-0000-0000-0000-000000000000&response_type=code&sso_reload=true
   ```


   Where `00000000-0000-0000-0000-000000000000` should be replaced with your Application ID.


   After selecting the consent link, sign into the customer's tenant, and then grant consent for the application.


   [![The Accept button](https://learn.microsoft.com/en-us/defender-endpoint/media/app-consent-partner.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/app-consent-partner.png#lightbox)


   In addition, you'll need to ask your customer for their tenant ID and save it for future use when acquiring the token.

6. **Done!** You successfully registered an application! See the following examples for token acquisition and validation.

## Get an access token example

To get access token on behalf of your customer, use the customer's tenant ID on the following token acquisitions.

For more information on Microsoft Entra token, see [Microsoft Entra tutorial](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

Tip

Some Microsoft Defender for Endpoint APIs continue to require access tokens issued for the legacy resource `https://api.securitycenter.microsoft.com`. If the token audience doesn't match the resource expected by the API, requests fail with `403 Forbidden`, even if the API endpoint uses `https://api.security.microsoft.com`. Use `https://api.securitycenter.microsoft.com` as the resource or scope when acquiring tokens.

### Using PowerShell

```powershell
# This code gets the application context token and saves it to a file named "Latest-token.txt" in the current directory.

$tenantId = '' ### Paste your tenant ID here.
$appId = '' ### Paste your Application (client) ID here.
$appSecret = '' ### Paste your Application secret (App key) here to test, and then store it in a safe place!

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
  resource = "$resourceAppIdUri"
  client_id = "$appId"
  client_secret = "$appSecret"
  grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$token = $authResponse.access_token
Out-File -FilePath "./Latest-token.txt" -InputObject $token
return $token
```

### Using C#

Important

The [Microsoft.IdentityModel.Clients.ActiveDirectory](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory) NuGet package and Azure AD Authentication Library \(ADAL\) have been deprecated. No new features have been added since June 30, 2020. To upgrade, see the [migration guide](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-migration).

1. Create a new Console Application.
2. Install NuGet [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client/).
3. Add the following using code:

   ```console
    using Microsoft.Identity.Client;
   ```


   This code was tested with NuGet `Microsoft.Identity.Client`.

4. Copy/Paste the following code in your application \(don't forget to update the three variables: `tenantId`, `appId`, and `appSecret`\).

   ```csharp
   string tenantId = "00000000-0000-0000-0000-000000000000"; // Paste your own tenant ID here
   string appId = "11111111-1111-1111-1111-111111111111"; // Paste your own app ID here
   string appSecret = "22222222-2222-2222-2222-222222222222"; // Paste your own app secret here for a test, and then store it in a safe place!
   const string authority = https://login.microsoftonline.com;
   const string audience = https://api.security.microsoft.com;

   IConfidentialClientApplication myApp = ConfidentialClientApplicationBuilder.Create(appId).WithClientSecret(appSecret).WithAuthority($"{authority}/{tenantId}").Build();

   List<string> scopes = new List<string>() { $"{audience}/.default" };

   AuthenticationResult authResult = myApp.AcquireTokenForClient(scopes).ExecuteAsync().GetAwaiter().GetResult();

   string token = authResult.AccessToken;
   ```

### Using Python

See [Get token using Python](https://learn.microsoft.com/en-us/defender-endpoint/api/run-advanced-query-sample-python#get-token).

### Using Curl

Note

The following procedure supposed Curl for Windows is already installed on your computer

1. Open a command window.
2. Set `CLIENT_ID` to your Azure application ID.
3. Set `CLIENT_SECRET` to your Azure application secret.
4. Set `TENANT_ID` to the Azure tenant ID of the customer that wants to use your application to access Microsoft Defender for Endpoint application.
5. Run the following command:

   ```curl
   curl -i -X POST -H "Content-Type:application/x-www-form-urlencoded" -d "grant_type=client_credentials" -d "client_id=%CLIENT_ID%" -d "scope=https://api.securitycenter.microsoft.com/.default" -d "client_secret=%CLIENT_SECRET%" "https://login.microsoftonline.com/%TENANT_ID%/oauth2/v2.0/token" -k
   ```


   You get an answer that resembles the following code snippet:


   ```console
   {"token_type":"Bearer","expires_in":3599,"ext_expires_in":0,"access_token":"eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIn <truncated> aWReH7P0s0tjTBX8wGWqJUdDA"}
   ```

## Validate the token

Confirm you received a correct token.

1. Copy/paste into [JWT](https://jwt.ms) the token you get in the previous step in order to decode it.
2. Confirm you get a roles claim with the appropriate permissions.

   In the following screenshot, you can see a decoded token acquired from an Application with multiple permissions to Microsoft Defender for Endpoint:

   [![The token validation page](https://learn.microsoft.com/en-us/defender-endpoint/media/webapp-decoded-token.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/webapp-decoded-token.png#lightbox)

   The "tid" claim is the tenant ID the token belongs to.

## Use the token to access Microsoft Defender for Endpoint API

1. Choose the API you want to use. For more information, see [Supported Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-list).
2. Set the Authorization header in the Http request you send to `Bearer {token}` \(Bearer is the Authorization scheme\). The Expiration time of the token is one hour \(you can send more than one request with the same token\).

   Here's an example of sending a request to get a list of alerts using C#:

   ```csharp
   var httpClient = new HttpClient();

   var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/alerts");

   request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

   var response = httpClient.SendAsync(request).GetAwaiter().GetResult();

    // Do something useful with the response
   ```

## See also

- [Supported Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-list)
- [Access Microsoft Defender for Endpoint on behalf of a user](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-nativeapp)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
