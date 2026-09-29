<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/api-create-app-user-context -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Create an app to access Microsoft Defender XDR APIs on behalf of a user

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Create an application to get programmatic access to Microsoft Defender on behalf of a single user.

If you need programmatic access to Microsoft Defender without a defined user \(for example, if you're writing a background app or daemon\), see [Create an app to access Microsoft Defender without a user](https://learn.microsoft.com/en-us/defender-xdr/api-create-app-web). If you need to provide access for multiple tenants—for example, if you're serving a large organization or a group of customers—see [Create an app with partner access to Microsoft Defender APIs](https://learn.microsoft.com/en-us/defender-xdr/api-partner-access). If you're not sure which kind of access you need, see [Get started](https://learn.microsoft.com/en-us/defender-xdr/api-access).

Microsoft Defender exposes much of its data and actions through a set of programmatic APIs. Those APIs help you automate workflows and make use of Microsoft Defender's capabilities. This API access requires OAuth2.0 authentication. For more information, see [OAuth 2.0 Authorization Code Flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

In general, you'll need to take the following steps to use these APIs:

- Create a Microsoft Entra application.
- Get an access token using this application.
- Use the token to access Microsoft Defender API.

This article explains how to:

- Create a Microsoft Entra application
- Get an access token to Microsoft Defender
- Validate the token

Note

When accessing Microsoft Defender API on behalf of a user, you need the correct application permissions and user permissions.

Tip

If you have the permission to perform an action in the portal, you have the permission to perform the action in the API. For more information about roles and permissions, see [Manage access to Microsoft Defender with Microsoft Entra global roles](https://learn.microsoft.com/en-us/defender-xdr/m365d-permissions).

## Create an app

1. Sign in to [Azure](https://portal.azure.com).
2. Navigate to **Microsoft Entra ID** > **App registrations** > **New registration**.

   [![The New registration option in the Manage pane in the Azure portal](https://learn.microsoft.com/en-us/defender/media/atp-azure-new-app2.png)](https://learn.microsoft.com/en-us/defender/media/atp-azure-new-app2.png#lightbox)
3. In the form, choose a name for your application and enter the following information for the redirect URI, then select **Register**.

   [![The application registration pane in the Azure portal](https://learn.microsoft.com/en-us/defender-xdr/media/api-create-app-user-context/nativeapp-create2.png)](https://learn.microsoft.com/en-us/defender-xdr/media/api-create-app-user-context/nativeapp-create2.png#lightbox)

   - **Application type:** Public client
   - **Redirect URI:** [https://portal.azure.com](https://portal.azure.com)

4. On your application page, select **API Permissions** > **Add permission** > **APIs my organization uses** >, type **Microsoft Threat Protection**, and select **Microsoft Threat Protection**. Your app can now access Microsoft Defender XDR.

   Tip

   *Microsoft Threat Protection* is a former name for Microsoft Defender XDR, and will not appear in the original list. You need to start writing its name in the text box to see it appear.

   [![Your organization's APIs pane in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender/media/apis-in-my-org-tab.PNG)](https://learn.microsoft.com/en-us/defender/media/apis-in-my-org-tab.PNG#lightbox)

   - Choose **Delegated permissions**. Choose the relevant permissions for your scenario \(for example **Incident.Read**\), and then select **Add permissions**.

     [![The Delegated permissions pane in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/api-create-app-user-context/request-api-permissions-delegated.png)](https://learn.microsoft.com/en-us/defender-xdr/media/api-create-app-user-context/request-api-permissions-delegated.png#lightbox)


   Note


   You need to select the relevant permissions for your scenario. *Read all incidents* is just an example. To determine which permission you need, please look at the **Permissions** section in the API you want to call.


   For instance, to [run advanced queries](https://learn.microsoft.com/en-us/defender-xdr/api-advanced-hunting), select the 'Run advanced queries' permission; to [isolate a device](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/isolate-machine), select the 'Isolate machine' permission.

5. Select **Grant admin consent**. Every time you add a permission, you must select **Grant admin consent** for it to take effect.

   [![The admin consent-granting pane in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/api-create-app-user-context/grant-consent-delegated.png)](https://learn.microsoft.com/en-us/defender-xdr/media/api-create-app-user-context/grant-consent-delegated.png#lightbox)
6. Record your application ID and your tenant ID somewhere safe. They're listed under **Overview** on your application page.

   [![The Overview pane in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender/media/app-and-tenant-ids.png)](https://learn.microsoft.com/en-us/defender/media/app-and-tenant-ids.png#lightbox)

## Get an access token

For more information on Microsoft Entra tokens, see the [Microsoft Entra tutorial](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-client-creds).

### Get an access token on behalf of a user using PowerShell

Use the MSAL.PS library to acquire access tokens with Delegated permissions. Run the following commands to get access token on behalf of a user:

```PowerShell
Install-Module -Name MSAL.PS # Install the MSAL.PS module from PowerShell Gallery

$TenantId = " " # Paste your directory (tenant) ID here.
$AppClientId="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" # Paste your application (client) ID here.

$MsalParams = @{
   ClientId = $AppClientId
   TenantId = $TenantId
   Scopes   = 'https://graph.microsoft.com/User.Read.All','https://graph.microsoft.com/Files.ReadWrite','https://api.securitycenter.windows.com/AdvancedQuery.Read'
}

$MsalResponse = Get-MsalToken @MsalParams
$AccessToken  = $MsalResponse.AccessToken
 
$AccessToken # Display the token in PS console
```

## Validate the token

1. Copy and paste the token into [JWT](https://jwt.ms) to decode it.
2. Make sure that the *roles* claim within the decoded token contains the desired permissions.

In the following image, you can see a decoded token acquired from an app, with `Incidents.Read.All`, `Incidents.ReadWrite.All`, and `AdvancedHunting.Read.All` permissions:

[![The permissions section in the Decoded Token pane in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender/media/defender-endpoint/webapp-decoded-token.png)](https://learn.microsoft.com/en-us/defender/media/defender-endpoint/webapp-decoded-token.png#lightbox)

## Use the token to access the Microsoft Defender API

1. Choose the API you want to use \(incidents, or advanced hunting\). For more information, see [Supported Microsoft Defender APIs](https://learn.microsoft.com/en-us/defender-xdr/api-supported).
2. In the http request you're about to send, set the authorization header to `"Bearer" <token>`, *Bearer* being the authorization scheme, and *token* being your validated token.
3. The token will expire within one hour. You can send more than one request during this time with the same token.

The following example shows how to send a request to get a list of incidents **using C#**.

```C#
    var httpClient = new HttpClient();
    var request = new HttpRequestMessage(HttpMethod.Get, "https://api.security.microsoft.com/api/incidents");

    request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", token);

    var response = httpClient.SendAsync(request).GetAwaiter().GetResult();
```

## Related articles

- [Microsoft Defender APIs overview](https://learn.microsoft.com/en-us/defender-xdr/api-overview)
- [Access the Microsoft Defender APIs](https://learn.microsoft.com/en-us/defender-xdr/api-access)
- [Create a 'Hello world' app](https://learn.microsoft.com/en-us/defender-xdr/api-hello-world)
- [Create an app to access Microsoft Defender XDR without a user](https://learn.microsoft.com/en-us/defender-xdr/api-create-app-web)
- [Create an app with multi-tenant partner access to Microsoft Defender XDR APIs](https://learn.microsoft.com/en-us/defender-xdr/api-partner-access)
- [Learn about API limits and licensing](https://learn.microsoft.com/en-us/legal/microsoft-365/api-terms)
- [Understand error codes](https://learn.microsoft.com/en-us/defender-xdr/api-error-codes)
- [OAuth 2.0 authorization for user sign in and API access](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-code)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
