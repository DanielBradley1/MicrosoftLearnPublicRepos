<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/quickstart-python -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Sign in users and call downstream APIs with the Microsoft Entra ID Auth SDK \(sidecar\) in Python

In this quickstart, you use a sample web app to learn how to sign in users or agents and call downstream APIs by using its own identity. The sample app uses the Microsoft Entra ID Auth SDK \(sidecar\) to validate user tokens for delegated access and uses application identity for service-to-service communication with downstream APIs like Microsoft Graph.

## Prerequisites

- Install the [UV package manager](https://github.com/astral-sh/uv). UV is a fast Python package installer and resolver written in Rust.
- Install [Docker Desktop](https://www.docker.com/products/docker-desktop/).
- An Azure account with an active subscription. If you don't already have one, [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- This Azure account must have permissions to manage applications. Any of the following Microsoft Entra roles include the required permissions:

  - Application Administrator
  - Application Developer

- A workforce tenant. You can use your Default Directory or [set up a new tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).

## Create and configure your Microsoft Entra application

To complete the rest of the quickstart, you need to first register an application in Microsoft Entra ID.

### Create application registration

Follow these steps to create the app registration:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Application Developer](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-developer).
2. If you have access to multiple tenants, use the **Settings** icon ![](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/media/common/admin-center-settings-icon.png) in the top menu to switch to the tenant in which you want to register the application.
3. Browse to **Entra ID** > **App registrations** and select **New registration**.
4. Enter a meaningful **Name** for your app, such as *identity-client-app*. App users see this name, and you can change it at any time. You can have multiple app registrations with the same name.
5. Under **Supported account types**, specify who can use the application. Select **Accounts in this organizational directory only** for most applications. Refer to the table for more information on each option.
   | Supported account types | Description |
   | --- | --- |
   | **Accounts in this organizational directory only** | For *single-tenant* apps for use only by users \(or guests\) in *your* tenant. |
   | **Accounts in any organizational directory** | For *multitenant* apps and you want users in *any* Microsoft Entra tenant to be able to use your application. Ideal for software-as-a-service \(SaaS\) applications that you intend to provide to multiple organizations. |
   | **Accounts in any organizational directory and personal Microsoft accounts** | For *multitenant* apps that support both organizational and personal Microsoft accounts \(for example, Skype, Xbox, Live, Hotmail\). |
   | **Personal Microsoft accounts** | For apps used only by personal Microsoft accounts \(for example, Skype, Xbox, Live, Hotmail\). |
6. Select **Register** to complete the app registration.

   ![Screenshot of Microsoft Entra admin center in a web browser, showing the Register an application pane.](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/media/quickstart-register-app/portal-02-app-reg-01.png)
7. The application's **Overview** page is displayed. Record the following values from the application Overview page for later use:

   - Application \(client\) ID
   - Directory \(tenant\) ID


   ![Screenshot of the Microsoft Entra admin center in a web browser, showing an app registration's Overview pane.](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/media/quickstart-register-app/portal-03-app-reg-02.png)

### Add a redirect URI

The Python sample app uses interactive authentication with a browser-based sign-in flow. Configure a redirect URI to handle the authentication response:

1. In your app registration, under **Manage**, select **Authentication**.
2. Select **Add a platform**.
3. Select **Mobile and desktop applications**.
4. Under **Custom redirect URIs**, enter `http://localhost`.
5. Select **Configure**.

### Add client credentials

The Microsoft Entra ID Auth SDK \(sidecar\) uses client credentials to authenticate and get tokens for downstream APIs. For local development and testing, use a self-signed certificate for authentication.

#### Generate a self-signed certificate

Run PowerShell as an administrator and use the following commands to generate a self-signed certificate:

```powershell
# Generate a self-signed certificate
$cert = New-SelfSignedCertificate `
    -Subject "CN=AgentID-Client-Certificate" `
    -CertStoreLocation "Cert:\CurrentUser\My" `
    -KeyExportPolicy Exportable `
    -KeySpec Signature `
    -KeyLength 2048 `
    -KeyAlgorithm RSA `
    -HashAlgorithm SHA256 `
    -NotAfter (Get-Date).AddDays(7)

# Export public key (CER) for upload to Azure
$cerPath = "agentid-client-certificate.cer"
Export-Certificate -Cert $cert -FilePath $cerPath

# Export private key (PFX) for the Entra ID Auth SDK (sidecar) container
# Replace <your-pfx-password> with a strong password and store it securely (for example, in a secret store).
$pfxPath = "agentid-client-certificate.pfx"
$certPassword = ConvertTo-SecureString -String "<your-pfx-password>" -Force -AsPlainText
Export-PfxCertificate -Cert $cert -FilePath $pfxPath -Password $certPassword

Write-Host "Certificate generated successfully!"
Write-Host "CER file (public key): $cerPath"
Write-Host "PFX file (private key): $pfxPath"
Write-Host "Certificate Thumbprint: $($cert.Thumbprint)"
```

Record the certificate thumbprint displayed in the PowerShell output. You need it to verify the certificate in the Microsoft Entra admin center matches the one installed locally.

#### Upload the certificate to Microsoft Entra ID

Follow these steps to upload the `.cer` file created in your current directory to the Microsoft Entra admin center:

1. Open your app registration in the Microsoft Entra admin center
2. Under **Manage**, select **Certificates & secrets**.
3. In the **Certificates** tab, select **Upload certificate**.
4. Select the `.cer` file you generated \(for example, `agentid-client-cert.cer`\).
5. Provide a description \(for example, "AgentID Local Development Certificate"\).
6. Select **Add**.
7. Record the certificate **Thumbprint** displayed \(it should match the one from your certificate generation\).

Note

For production environments, use certificates issued by a trusted Certificate Authority \(CA\) and store them in Azure Key Vault with managed identity access. Use self-signed certificates only for local development and testing.

### Configure API permissions

Follow these steps to configure delegated permissions to Microsoft Graph. With these permissions, your client application can perform operations on behalf of the signed-in user, such as reading their email.

1. In your app registration, under **Manage**, select **API permissions** > **Add a permission** > **Microsoft Graph**.
2. Select **Delegated permissions**. Microsoft Graph exposes many permissions, with the most commonly used shown at the top of the list.
3. Under **Select permissions**, select and add **User.Read**.

### Configure application permissions

To test application-only flows where the Entra ID Auth SDK \(sidecar\) calls APIs by using its own identity \(without a user context\), configure application permissions:

1. From the **API permissions** page, select **Add a permission** > **Microsoft Graph**.
2. Select **Application permissions**.
3. Under **Select permissions**, search for and select **User.Read.All**.
4. Select **Add permissions**.
5. Select **Grant admin consent for \[Your Tenant\]** and confirm.

Note

Application permissions require administrator consent. Without this step, the application-only endpoints in the testing section fail.

### Expose an API \(for token validation testing\)

To call the Entra ID Auth SDK \(sidecar\)'s `/validate` endpoint with tokens issued specifically for your application \(using the `api://<application-client-id>/access_as_user` scope\), you **must** complete this step. If you're only testing Microsoft Graph scenarios with delegated permissions, you can skip this section. Follow these steps to expose an API containing the required scopes:

1. Under **Manage**, select **Expose an API**.
2. At the top of the page, select **Add** next to **Application ID URI**. This value defaults to `api://<application-client-id>`. The App ID URI acts as the prefix for the scopes you'll reference in your API's code, and it must be globally unique. Select **Save**.
3. Select **Add a scope** as shown:

   ![Screenshot of an app registration's Expose an API pane in the Microsoft Entra admin center.](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/media/quickstart-register-app/portal-02-expose-api.png)
4. Next, specify the scope's attributes in the **Add a scope** pane, as follows:

   - **Scope name**: `access_as_user`
   - **Who can consent**: Admins and users
   - **Admin consent display name**: Access the Entra ID Auth SDK \(sidecar\) as user
   - **Admin consent description**: Allow access to Entra ID Auth SDK \(sidecar\) APIs as the signed-in user
   - **State**: Enabled

5. Select **Add scope**.

## Start the Microsoft Entra ID Auth SDK \(sidecar\)

The Microsoft Entra ID Auth SDK \(sidecar\) is a containerized web service that handles token acquisition, validation, and secure downstream API calls. It runs as a companion container alongside your application, allowing you to offload identity logic to a dedicated service.

### Create a configuration file

The Entra ID Auth SDK \(sidecar\) requires a configuration file to connect to your Microsoft Entra application. Create a new directory for your configuration and create an `appsettings.json` file:

```powershell
# Create a directory for the Entra ID Auth SDK (sidecar) configuration
New-Item -ItemType Directory -Path "agentid-config" -Force
cd agentid-config

# Create the appsettings.json file
New-Item -ItemType File -Path "appsettings.json"
```

Open `appsettings.json` in your preferred text editor and add the following configuration, replacing the placeholder values with your Microsoft Entra application details:

```json
{
    "AzureAd": {
        "Instance": "https://login.microsoftonline.com/",
        "TenantId": "YOUR_TENANT_ID_HERE",
        "ClientId": "YOUR_CLIENT_ID_HERE",
        "ClientCredentials": [
            {
                "SourceType": "Path",
                "CertificateStorePath": "agentid-client-certificate.pfx",
                "CertificateDistinguishedName": "<your-pfx-password>"
            }
        ]
    },
    "DownstreamApis": {
        "me": {
            "BaseUrl": "https://graph.microsoft.com/v1.0/",
            "RelativePath": "me",
            "Scopes": [ "User.Read" ]
        }
    },
    "Logging": {
        "LogLevel": {
            "Default": "Information",
            "Microsoft.AspNetCore": "Warning"
        }
    },
    "AllowedHosts": "*"
}
```

### Pull and run the Entra ID Auth SDK \(sidecar\) container

The Entra ID Auth SDK \(sidecar\) is available as a prebuilt container image from the [Microsoft Container Registry \(MCR\)](https://mcr.microsoft.com/en-us/artifact/mar/entra-sdk/auth-sidecar). Before pulling the container image, verify that Docker Desktop is running. If Docker isn't running, open Docker Desktop and wait for the status to show "Docker Desktop is running".

Navigate to your configuration directory and run the following commands:

```powershell
# Navigate to your config directory
cd agentid-config

# Pull the Entra ID Auth SDK (sidecar) container image from MCR
docker pull mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0-rc.2-azurelinux3.0-distroless

# Run the container
docker run -d `
    --name agentid-sdk `
    -p 5178:8080 `
    -e ASPNETCORE_ENVIRONMENT=Development `
    mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0-rc.2-azurelinux3.0-distroless

# Copy configuration files into the container
docker cp appsettings.json agentid-sdk:/app/appsettings.json
docker cp agentid-client-certificate.pfx agentid-sdk:/app/agentid-client-certificate.pfx

# Restart the container to apply the configuration
docker restart agentid-sdk
```

Note

For Windows hosts, use the Windows container variant: `mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0-rc.2-windows`

You can manage the Entra ID Auth SDK \(sidecar\) container by using the following Docker commands:

- **View container logs**: `docker logs agentid-sdk`
- **View real-time logs**: `docker logs -f agentid-sdk`
- **Stop the container**: `docker stop agentid-sdk`
- **Start the container again**: `docker start agentid-sdk`
- **Remove the container**: `docker rm agentid-sdk`

### Verify that the container is running

You can verify whether the Entra ID Auth SDK \(sidecar\) container is running correctly by calling the health check endpoint,`/healthz`:

```powershell
Invoke-RestMethod -Uri "http://localhost:5178/healthz" -ErrorAction SilentlyContinue
```

This endpoint returns `Healthy`, which confirms the Entra ID Auth SDK \(sidecar\) is running correctly and ready to handle requests. Don't terminate the Entra ID Auth SDK \(sidecar\) while testing. The container must continue running in the background for all authentication and API calls from the Python app to work.

## Run the Python sample app

The Python sample app demonstrates how to use the Microsoft Entra ID Auth SDK \(sidecar\) for authentication and API calls. The Entra ID Auth SDK \(sidecar\) runs as a local web service and acts as an authentication proxy. It validates user tokens and calls downstream APIs like Microsoft Graph on your behalf.

The sample includes Python scripts that show two authentication patterns:

- **Delegated permissions**: The Entra ID Auth SDK \(sidecar\) validates your user token and calls APIs on behalf of the signed-in user.
- **Application permissions**: The Entra ID Auth SDK \(sidecar\) uses its own identity to call APIs without a user context.

This approach centralizes token management and API access in a single service that your applications can consume through simple HTTP requests.

### Clone or download the Python sample app

[Download the Python sample app](https://github.com/AzureAD/microsoft-identity-web/tree/master/tests/DevApps/SidecarAdapter/python) and extract it to a local directory. Alternatively, clone the repository by opening a command prompt, navigating to your desired project location, and running the following command:

```powershell
git clone https://github.com/AzureAD/microsoft-identity-web.git
cd microsoft-identity-web/tests/DevApps/SidecarAdapter/python
```

The sample app contains the following Python scripts:

- `get_token.py` – Acquires user access tokens through the Microsoft Authentication Library \(MSAL\).
- `main.py` – Command-line interface that calls the Entra ID Auth SDK \(sidecar\) endpoints and displays JSON responses.
- `MicrosoftIdentityWebSidecarClient.py` – HTTP client wrapper for the Entra ID Auth SDK \(sidecar\)'s `/Validate`, `/AuthorizationHeader`, and `/DownstreamApi` endpoints.

The Python scripts use the parameter `me` when calling Entra ID Auth SDK \(sidecar\) endpoints. This parameter references the downstream API configuration named "me" in the Entra ID Auth SDK \(sidecar\)s `appsettings.json`:

```json
"DownstreamApis": {
    "me": {
        "BaseUrl": "https://graph.microsoft.com/v1.0/",
        "RelativePath": "me",
        "Scopes": [ "User.Read" ]
    }
}
```

When you call an Entra ID Auth SDK \(sidecar\) endpoint with the `me` parameter, the SDK uses the base URL and relative path from the configuration to construct the full API endpoint, requests the specified scopes, and calls the Microsoft Graph `/me` endpoint to retrieve the signed-in user's profile. You can add additional downstream API configurations to `appsettings.json` with different names and endpoints to call additional APIs.

## Test interaction between the Microsoft Entra ID Auth SDK \(sidecar\) and the Python app

This quickstart demonstrates a three-tier authentication pattern:

1. **User authentication**: You acquire a user access token by using MSAL for Python. This token proves the user's identity.
2. **Token validation**: The Entra ID Auth SDK \(sidecar\) validates the user token to ensure it's authentic and issued for your application.
3. **Token exchange**: The Entra ID Auth SDK \(sidecar\) uses the On-Behalf-Of \(OBO\) flow to exchange the user token for a new token scoped to Microsoft Graph, then calls the API.

For application-only scenarios, the Entra ID Auth SDK \(sidecar\) bypasses user authentication and uses its own client credentials to acquire tokens directly. The SDK centralizes this authentication logic, so your Python application only needs to make simple HTTP requests without managing complex OAuth flows.

### Acquire a user access token

Before testing the Entra ID Auth SDK \(sidecar\) endpoints, obtain a valid access token. The `get_token.py` script uses MSAL for Python to acquire tokens interactively through a browser-based sign-in flow.

**Token scopes and audiences:**

The scope you request determines the token's audience \(`aud` claim\), which must match the endpoint you're calling:

- **For token validation testing**, use `api://<client-id>/access_as_user` to test the `/validate` endpoint
- **For Microsoft Graph testing**, acquire a new token with `User.Read` scope to test `/authorizationheader` and `/downstreamapi` endpoints

Use the following commands to set your configuration variables and acquire a token:

```powershell
# Set your configuration
$clientId = "YOUR_CLIENT_ID_HERE"
$tenantId = "YOUR_TENANT_ID_HERE"
$authority = "https://login.microsoftonline.com/$tenantId"

# For testing Entra ID Auth SDK (sidecar) APIs (if you exposed the API)
$scope = "api://$clientId/access_as_user"

# Or for testing Microsoft Graph directly
# $scope = "User.Read"

# Acquire token
$token = uv run --with msal get_token.py --client-id $clientId --authority $authority --scope $scope
```

When you run the acquire token command, the script initiates an interactive browser-based sign-in flow. This browser authentication only occurs on the first run. After successful authentication, the token is cached locally for subsequent use. The access token is then printed to the console and stored in the `$token` PowerShell variable for use in subsequent commands.

### Test the Microsoft Entra ID Auth SDK \(sidecar\) endpoints with delegated permissions

After you get a valid user token, you can test the Entra ID Auth SDK \(sidecar\) core endpoints. These operations use delegated permissions, so the SDK acts on behalf of the signed-in user.

First, set the SDK's base URL:

```powershell
$side_car_url = "http://localhost:5178"
```

#### 1. Validate the user token

The `/validate` endpoint requires a token issued specifically for your application by using the `api://<client-id>/access_as_user` scope. Before you test token validation, ensure you complete the steps in the "Expose an API" section. Use the following command to call the `/validate` endpoint.

```powershell
uv run --with requests main.py --base-url $side_car_url --authorization-header "Bearer $token" validate
```

**Expected response:**

The `/validate` endpoint checks that the token is valid and extracts claims information:

```json
{
  "protocol": "Bearer",
  "token": "eyJ0eXAiOiJKV1QiLCJub25jZSI6...",
  "claims": {
    "aud": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
    "iss": "https://login.microsoftonline.com/...",
    "name": "Your Name",
    "upn": "your.email@domain.com"
  }
}
```

This response confirms that:

- The token format is correct \(Bearer token\)
- The token is issued by the expected authority
- The audience \(`aud`\) matches your application
- User identity claims are present and valid

#### 2. Get an authorization header for Microsoft Graph

The `/authorizationheader` endpoint retrieves a properly formatted authorization header for calling downstream APIs:

```powershell
uv run --with requests main.py --base-url $side_car_url --authorization-header "Bearer $token" get-auth-header me
```

This endpoint:

- Validates the incoming user token
- Acquires a new token for Microsoft Graph on behalf of the user
- Returns the formatted authorization header

#### 3. Call Microsoft Graph through the Microsoft Entra ID Auth SDK \(sidecar\)

The `/downstreamapi` endpoint calls Microsoft Graph directly and returns the response:

```powershell
uv run --with requests main.py --base-url $side_car_url --authorization-header "Bearer $token" invoke-downstream me
```

**Expected response:**

```json
{
  "statusCode": 200,
  "headers": {...},
  "content": {
    "displayName": "Your Name",
    "mail": "your.email@domain.com",
    "userPrincipalName": "your.email@domain.com"
  }
}
```

The `me` parameter corresponds to the downstream API configuration you defined in `appsettings.json`. The Entra ID Auth SDK \(sidecar\):

1. Validates your user token
2. Acquires a new token for Microsoft Graph by using the on-behalf-of \(OBO\) flow
3. Calls the `/me` endpoint on Microsoft Graph
4. Returns the user profile data

#### 4. Override default scopes and supply a request body

You can customize API calls by overriding the default scopes configured in `appsettings.json` or by providing a request body for write operations.

```powershell
uv run --with requests main.py --base-url $side_car_url --authorization-header "Bearer $token" --scope <scopes> invoke-downstream <api-name> --body-file <path-to-file>
```

This approach is useful when:

- Testing different permission levels. For example, you can specify different scopes like --scope `User.Read Mail.Read` to request additional permissions
- The downstream API requires scopes not configured by default
- You need to request additional permissions dynamically
- When calling APIs that require a request body \(such as creating or updating resources\), you add the optional `--body-file` parameter used for POST/PUT operations

### Test application-only endpoints

The Microsoft Entra ID Auth SDK \(sidecar\) also supports application-only flows. In these flows, the Entra ID Auth SDK \(sidecar\) uses its own app identity instead of acting on behalf of a user. These endpoints don't require a user authorization header.

Note

Application-only flows require that your app registration has **application permissions** \(such as `User.Read.All`\) in Microsoft Entra ID, not just delegated permissions. An administrator must grant consent to these permissions before you can test these endpoints.

#### Get authorization header without user context

Use this endpoint to retrieve an authorization header for calling Microsoft Graph with the Entra ID Auth SDK \(sidecar\)'s own identity:

```powershell
uv run --with requests main.py --base-url $side_car_url get-auth-header-unauth me
```

This endpoint:

- Uses the Entra ID Auth SDK \(sidecar\)'s client credentials \(app identity\) to authenticate.
- Acquires an app-only access token for Microsoft Graph
- Returns the authorization header

#### Call Microsoft Graph without user context

Use this endpoint to call Microsoft Graph directly by using the Entra ID Auth SDK \(sidecar\) identity:

```powershell
uv run --with requests main.py --base-url $side_car_url invoke-downstream-unauth me
```

This example demonstrates service-to-service communication where:

- No user is involved in the authentication flow
- The Entra ID Auth SDK \(sidecar\) authenticates by using its own client ID and certificate
- The API call uses application permissions, not delegated permissions
- This pattern is ideal for background services, batch processing, or automated tasks

### Understand the responses

#### Token validation response structure

The validation response provides detailed information about the token:

| Field | Description |
| --- | --- |
| `protocol` | The authentication scheme \(always "Bearer" for OAuth 2.0 tokens\) |
| `token` | The original access token \(truncated in examples\) |
| `claims` | Key-value pairs extracted from the token's payload |
| `claims.aud` | The intended audience \(your client ID\) |
| `claims.iss` | The token issuer \(Microsoft Entra ID\) |
| `claims.name` | The display name of the signed-in user |
| `claims.upn` | User Principal Name \(email address\) |

#### Microsoft Graph call response structure

| Field | Description |
| --- | --- |
| `statusCode` | HTTP status code from Microsoft Graph \(200 = success\) |
| `headers` | Response headers from the API call |
| `content` | The actual data returned by Microsoft Graph |
| `content.displayName` | User's display name in the directory |
| `content.mail` | User's email address |
| `content.userPrincipalName` | User's UPN |

### Troubleshooting common issues

If you encounter errors when testing the Microsoft Entra ID Auth SDK \(sidecar\) endpoints, check the following solutions to common issues:

| Issue | Solution |
| --- | --- |
| **"Connection refused" errors** | Verify the Entra ID Auth SDK \(sidecar\) container is running: `docker ps -a`. If the container status shows "Exited", check the logs: `docker logs agentid-sdk`. Restart the container: `docker start agentid-sdk` and test the health endpoint: `Invoke-RestMethod -Uri "http://localhost:5178/healthz"`. |
| **Container returns 500 Internal Server Error** | View container logs for detailed errors: `docker logs agentid-sdk`. Common causes: invalid JSON in `appsettings.json`, incorrect certificate path, wrong certificate password, or missing TenantId/ClientId values. |
| **Certificate not found errors** | Ensure the PFX file was copied correctly: `docker exec agentid-sdk ls -la /app/agentid-client-certificate.pfx`. If missing, copy it again: `docker cp agentid-client-certificate.pfx agentid-sdk:/app/agentid-client-certificate.pfx` and restart: `docker restart agentid-sdk`. |
| **"Invalid token" or "Audience validation failed" errors** | Ensure your token's audience \(`aud` claim\) matches your client ID. For the `/validate` endpoint, use the `api://<client-id>/access_as_user` scope. For Microsoft Graph calls, use `User.Read`. Clear the token cache: `Remove-Item -Path "$env:USERPROFILE\.msal_token_cache.bin" -ErrorAction SilentlyContinue`. |
| **appsettings.json not loading** | Verify the file was copied into the container: `docker exec agentid-sdk cat /app/appsettings.json`. Ensure the JSON is valid \(no comments, proper syntax\). If the file is missing or incorrect, copy it again and restart the container. |
| **Container won't start after configuration changes** | Stop and remove the container: `docker stop agentid-sdk && docker rm agentid-sdk`. Run the container again with updated configuration files following the "Pull and run the Entra ID Auth SDK \(sidecar\) container" section. |

## Related content

- [Quickstart: TypeScript](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/quickstart-typescript)
- [Agent Identities](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/agent-identities)
- [Configuration Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
- [Using from Python](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-python)
