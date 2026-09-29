<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/fetch-alerts-mssp -->
<!-- Sitemap-Last-Modified: 2026-09-22 -->

# Fetch Microsoft Defender alerts from an MSSP customer tenant

Note

The managed security service provider \(MSSP\) performs the configuration in this article. A Microsoft Entra administrator in each customer tenant grants the required application consent.

An MSSP can retrieve Microsoft Defender alerts from a customer tenant by using a supported security information and event management \(SIEM\) integration or the Microsoft Graph security API. Configure authorization separately for each customer tenant.

## Choose an alert retrieval method

Select the method that matches your security operations platform:

- **SIEM integration**: Use a supported connector to ingest Microsoft Defender XDR incidents and their correlated alerts. Some integrations also support streaming event data.
- **Microsoft Graph security API**: Use an MSSP-managed multitenant application to retrieve alerts directly from each customer tenant.

## Retrieve incidents and alerts through a SIEM

Follow [Integrate your SIEM tools with Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/configure-siem-defender) to select and configure a supported integration. Complete the connector authorization for each customer tenant.

The supported integrations use the Microsoft Defender XDR incidents REST API or the Microsoft Defender XDR Streaming API. Don't configure new integrations that depend on the legacy Defender for Endpoint SIEM API. For migration information, see [Migrate from the MDE SIEM API to the Microsoft Defender XDR alerts API](https://learn.microsoft.com/en-us/defender-endpoint/configure-siem).

## Retrieve alerts through the Microsoft Graph security API

Use application-level authorization for an unattended MSSP service or SIEM connector. With application-level authorization, the application permissions determine which security data the application can access.

### Prerequisites

Before you configure API access, make sure you have:

- An application registered in the MSSP's Microsoft Entra tenant. Configure the application as multitenant by selecting **Accounts in any organizational directory**.
- The Microsoft Graph `SecurityAlert.Read.All` application permission, which is the least-privileged permission for retrieving alerts.
- An application credential. For production applications, use a certificate or federated credential instead of a client secret when possible.
- A Microsoft Entra administrator in each customer tenant who can review the requested permissions and grant tenant-wide admin consent.

### Configure Microsoft Graph access

Configure the MSSP application and authorize it in each customer tenant:

1. [Register the application in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app). For **Supported account types**, select **Accounts in any organizational directory**, and record the **Application \(client\) ID**.
2. [Add a Microsoft Graph application permission](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-configure-app-access-web-apis#add-permissions-to-access-microsoft-graph), and select `SecurityAlert.Read.All`. The [List alerts\_v2 permissions](https://learn.microsoft.com/en-us/graph/api/security-list-alerts_v2#permissions) identify this permission as the least-privileged application permission for retrieving alerts.
3. [Add a certificate or federated credential](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-add-credentials) to the application. Protect the credential by using your organization's secret-management process.
4. Ask an authorized administrator in each customer tenant to [grant tenant-wide admin consent](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/grant-admin-consent) to the application. Consent is tenant-specific and must be granted again if the application requests more permissions.

   The administrator can use the following tenant-specific consent URL:

   `https://login.microsoftonline.com/<customer-tenant-id>/adminconsent?client_id=<application-client-id>`
5. Use the [OAuth 2.0 client credentials flow](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-client-creds-grant-flow) to request an application token from the customer tenant. Use `https://graph.microsoft.com/.default` as the scope.
6. Send the token as a bearer token in a request to `GET https://graph.microsoft.com/v1.0/security/alerts_v2`. For supported filters, pagination, response details, and examples, see [List alerts\_v2](https://learn.microsoft.com/en-us/graph/api/security-list-alerts_v2).
7. Repeat the consent and token-acquisition steps for each customer tenant. Store each customer tenant ID with the connector configuration so that token requests use the correct tenant endpoint.

## Identify a legacy SIEM API integration

The legacy setup used the [LoginBrowser.psm1 module](https://github.com/shawntabrizi/Microsoft-Authentication-with-PowerShell-and-MSAL/blob/master/Authorization%20Code%20Grant%20Flow/LoginBrowser.psm1) and a script named `MsspTokensAcquisition.ps1` to request delegated tokens for the retired Azure Active Directory Graph \(Azure AD Graph\) resource. Don't use this flow for new integrations. If an existing connector contains the following script, migrate it to a supported SIEM integration or the Microsoft Graph security API.

Note

The sample is retained only to help identify a legacy connector. It uses deprecated components and isn't a supported implementation.

1. Compare the existing connector with this legacy script:

   ```powershell
   param (
       [Parameter(Mandatory=$true)][string]$clientId,
       [Parameter(Mandatory=$true)][string]$secret,
       [Parameter(Mandatory=$true)][string]$tenantId
   )
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12

   # Load our Login Browser Function
   Import-Module .\LoginBrowser.psm1

   # Configuration parameters
   $login = "https://login.microsoftonline.com"
   $redirectUri = "https://SiemMsspConnector"
   $resourceId = "https://graph.windows.net"

   Write-Host 'Prompt the user for his credentials, to get an authorization code'
   $authorizationUrl = ("{0}/{1}/oauth2/authorize?prompt=select_account&response_type=code&client_id={2}&redirect_uri={3}&resource={4}" -f
                       $login, $tenantId, $clientId, $redirectUri, $resourceId)
   Write-Host "authorzationUrl: $authorizationUrl"

   # Fake a proper endpoint for the Redirect URI
   $code = LoginBrowser $authorizationUrl $redirectUri

   # Acquire token using the authorization code

   $Body = @{
       grant_type = 'authorization_code'
       client_id = $clientId
       code = $code
       redirect_uri = $redirectUri
       resource = $resourceId
       client_secret = $secret
   }

   $tokenEndpoint = "$login/$tenantId/oauth2/token?"
   $Response = Invoke-RestMethod -Method Post -Uri $tokenEndpoint -Body $Body
   $token = $Response.access_token
   $refreshToken= $Response.refresh_token

   Write-Host " ----------------------------------- TOKEN ---------------------------------- "
   Write-Host $token

   Write-Host " ----------------------------------- REFRESH TOKEN ---------------------------------- "
   Write-Host $refreshToken
   ```

The use of `https://graph.windows.net`, a delegated refresh token, and the external browser module identifies the legacy flow. Don't run the script or weaken the PowerShell execution policy to support it.

The legacy **SIEM** page and **Authorize application** action applied only to the deprecated Defender for Endpoint SIEM API. Current SIEM connectors and Microsoft Graph integrations use Microsoft Entra application consent instead.

## Related content

- [Grant MSSP access to the portal](https://learn.microsoft.com/en-us/defender-endpoint/grant-mssp-access)
- [Access the MSSP customer portal](https://learn.microsoft.com/en-us/defender-endpoint/access-mssp-portal)
- [Configure alert notifications](https://learn.microsoft.com/en-us/defender-endpoint/configure-mssp-notifications)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
