<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/quickstart-typescript -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Sign in users and call downstream APIs with the Microsoft Entra ID Auth SDK \(sidecar\) in TypeScript

In this quickstart, you use a sample web app to learn how to sign in users or agents and call downstream APIs by using its own identity. The sample app uses the Microsoft Entra ID Auth SDK \(sidecar\) to validate user tokens for delegated access and uses application identity for service-to-service communication with downstream APIs like Microsoft Graph.

## Prerequisites

- Install [Node.js 18.x](https://nodejs.org/en/download) or later.
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

The TypeScript sample app uses interactive authentication with a browser-based sign-in flow. Configure a redirect URI to handle the authentication response:

1. In your app registration, under **Manage**, select **Authentication**.
2. Select **Add a platform**.
3. Select **Mobile and desktop applications**.
4. Under **Custom redirect URIs**, enter `http://localhost`.
5. Select **Configure**.

### Add client credentials

The Microsoft Entra ID Auth SDK \(sidecar\) uses client credentials to authenticate and acquire tokens for downstream APIs. For local development and testing, use a self-signed certificate for authentication.

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

For production environments, use certificates issued by a trusted Certificate Authority \(CA\) and store them in Azure Key Vault with managed identity access. Self-signed certificates should only be used for local development and testing.

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

# Set the recommended sidecar image version
$sidecarVersion = "1.1.2-preview"
$sidecarImage = "mcr.microsoft.com/entra-sdk/auth-sidecar:${sidecarVersion}-azurelinux3.0-distroless"

# Pull the Entra ID Auth SDK (sidecar) container image from MCR
docker pull $sidecarImage

# Run the container
docker run -d `
    --name agentid-sdk `
    -p 5178:8080 `
    -e ASPNETCORE_ENVIRONMENT=Development `
    $sidecarImage

# Copy configuration files into the container
docker cp appsettings.json agentid-sdk:/app/appsettings.json
docker cp agentid-client-certificate.pfx agentid-sdk:/app/agentid-client-certificate.pfx

# Restart the container to apply the configuration
docker restart agentid-sdk
```

Note

For Windows hosts, set `$sidecarImage = "mcr.microsoft.com/entra-sdk/auth-sidecar:${sidecarVersion}-windows"` before pulling and running the container.

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

This endpoint returns `Healthy`, which confirms the Entra ID Auth SDK \(sidecar\) is running correctly and ready to handle requests. Don't terminate the Entra ID Auth SDK \(sidecar\) while testing. The container must continue running in the background for all authentication and API calls from the TypeScript sample app to work.

## Run the TypeScript sample app

The TypeScript sample app demonstrates how to use the Microsoft Entra ID Auth SDK \(sidecar\) to validate user tokens. The app is an Express.js server that validates incoming requests through the Entra ID Auth SDK \(sidecar\). The Entra ID Auth SDK \(sidecar\) can also call downstream APIs like Microsoft Graph on your behalf.

### Clone or download the sample app

[Download the TypeScript sample app](https://github.com/AzureAD/microsoft-identity-web/tree/master/tests/DevApps/SidecarAdapter/typescript) and extract it to a local directory. Alternatively, clone the repository by opening a command prompt, navigating to your desired project location, and running the following command:

```powershell
git clone https://github.com/AzureAD/microsoft-identity-web.git
```

After cloning the repo, navigate to the TypeScript sample app:

```powershell
cd microsoft-identity-web/tests/DevApps/SidecarAdapter/typescript
```

The TypeScript sample app consists of three main files that work together to demonstrate authentication patterns with the Microsoft Entra ID Auth SDK \(sidecar\).

**sidecar.ts**: Provides the `SidecarClient` class, which is a TypeScript client that communicates with the Entra ID Auth SDK \(sidecar\) container. It sends bearer tokens to the Entra ID Auth SDK \(sidecar\)'s `/Validate` endpoint, receives back the validated token along with user claims, and handles token validation errors.

**app.ts**: An Express.js web server that authenticates incoming requests. It extracts Bearer tokens or app-only SHR PoP credentials from the authorization header and validates them using `SidecarClient`. For PoP, it forwards `original-method` and `original-uri` so the sidecar can validate request binding. If the sidecar rejects the credential, the server propagates the sidecar's status code. A sidecar connectivity failure returns 502, while an unexpected application error returns 500. When validation succeeds, it attaches the returned claims to the request object through `req.sidecarValidation` for use in downstream route handlers.

Important

The development sample derives the external scheme and host from the incoming Express request. Before production use, replace those values with a canonical external origin from trusted configuration, and preserve the encoded request target at the trusted server or proxy boundary.

**sidecar.test.ts**: Contains automated integration tests that verify the complete authentication flow. The test suite starts by launching the Express server, then uses MSAL Node to perform interactive browser authentication and acquire an access token with the required scopes. It then makes an HTTP request to the server with the acquired token and verifies that the Entra ID Auth SDK \(sidecar\) validates the token correctly before returning the expected user claims.

### Install dependencies

Navigate to the TypeScript sample directory and install the required packages:

```powershell
cd d:\SDKs\microsoft-identity-web\tests\DevApps\SidecarAdapter\typescript
npm install
```

### Configure the sample app

Before running the sample app, configure it with your application details as follows:

1. Open `sidecar.test.ts` and update the client ID, tenant ID, and scopes to match your app registration.
2. Create a `.env` file in the `typescript` directory for environment variables:

   ```powershell
   # Create .env file
   New-Item -ItemType File -Path ".env" -Force
   ```


   Add the following configuration to `.env`:


   ```env
   PORT=5555
   SIDECAR_BASE_URL=http://localhost:5178
   ```

### Start the Express server

Start the TypeScript sample app by running `npm start`. The server starts on `http://localhost:5555` and is ready to accept authenticated requests. You should see output similar to:

```text
Server listening on port 5555
Sidecar base URL: http://localhost:5178
```

Keep this terminal window open. The Express server must continue running to handle test requests in the next section.

## Test the TypeScript sample app

Now that both the Entra ID Auth SDK \(sidecar\) container and the Express server are running, you can test the authentication and API call scenarios.

### Test with user-delegated permissions

This scenario shows how to sign in a user, acquire a token, and call the Express server with that token.

#### Acquire a user token

The sample includes an automated test that acquires a user token by using MSAL. Open a **new** PowerShell window \(keep the Express server running\) and run:

```powershell
cd d:\SDKs\microsoft-identity-web\tests\DevApps\SidecarAdapter\typescript
npm test
```

This command runs the integration test that:

1. Opens a browser window for interactive authentication
2. Acquires an access token with the `api://<your-client-id>/access_as_user` scope
3. Calls the Express server with the token
4. Checks that the Entra ID Auth SDK \(sidecar\) validates the token successfully

On the first run, you're prompted to sign in with your Microsoft Entra credentials. The browser window opens automatically. After successful authentication, you can close the browser.

#### Manual testing with curl

If you prefer manual testing, you can acquire a token and call the Express server directly:

```powershell
# First, get a token (you'll need to implement token acquisition or extract from test output)
$token = "YOUR_ACCESS_TOKEN_HERE"

# Call the Express server
Invoke-RestMethod -Uri "http://localhost:5555/api/protected" `
    -Headers @{ Authorization = "Bearer $token" } `
    -Method Get
```

The expected response is:

```json
message                                                  protocol token          claims
-------                                                  -------- -----          ------
Request authenticated via Microsoft Identity Web Sidecar Bearer   ***redacted*** @{aud=api://"Your client ID"; iss=https://sts.win…
```

### Test application-only authentication

This scenario demonstrates how to call downstream APIs by using the application's own identity without user context.

From your PowerShell window, call the Entra ID Auth SDK \(sidecar\) directly to test application-only flow:

```powershell
# Call Microsoft Graph using application identity
Invoke-RestMethod -Uri "http://localhost:5178/DownstreamApiUnauthenticated/me" `
    -Method Get
```

This endpoint:

1. Authenticates by using the application's certificate \(configured in `appsettings.json`\)
2. Acquires an app-only access token for Microsoft Graph
3. Calls the Graph API `/me` endpoint
4. Returns the service principal information

Note

This scenario requires the `User.Read.All` application permission with admin consent \(configured earlier in the quickstart\).

### Test custom downstream API calls

You can test custom downstream API configurations by adding them to the Entra ID Auth SDK \(sidecar\)'s `appsettings.json`:

```json
"DownstreamApis": {
    "me": {
        "BaseUrl": "https://graph.microsoft.com/v1.0/",
        "RelativePath": "me",
        "Scopes": [ "User.Read" ]
    },
    "users": {
        "BaseUrl": "https://graph.microsoft.com/v1.0/",
        "RelativePath": "users",
        "Scopes": [ "User.Read.All" ]
    }
}
```

Then restart the Entra ID Auth SDK \(sidecar\) container and test the new endpoint:

```powershell
# Restart container to reload configuration
docker restart agentid-sdk

# Test the new endpoint
Invoke-RestMethod -Uri "http://localhost:5178/DownstreamApiUnauthenticated/users" `
    -Method Get
```

## Related content

- [Quickstart: Python](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/quickstart-python)
- [Agent Identities](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/agent-identities)
- [Configuration Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
- [Using from TypeScript](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-typescript)
