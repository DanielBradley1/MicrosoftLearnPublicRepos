<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/authentication/client-secrets -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Use client secrets with Microsoft.Identity.Web

A client secret is a string value that your application uses to prove its identity when requesting tokens from the Microsoft identity platform. Microsoft.Identity.Web supports client secrets as one of several credential types for confidential client applications.

Important

Client secrets should only be used in **development and testing environments**. For production workloads, use [certificates](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificates) or [certificateless credentials](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificateless) such as managed identities or federated identity credentials. Client secrets are easier to compromise than certificate-based credentials and can't be scoped to specific operations.

## Choose a credential type

Confidential client applications need a credential to authenticate with the Microsoft identity platform. Microsoft.Identity.Web supports the following credential types through the `ClientCredentials` configuration section:

| Credential type | Recommended environment | Security level |
| --- | --- | --- |
| **Client secret** | Development, testing | Low |
| **Certificate** | Staging, production | High |
| **Managed identity** | Azure-hosted production | Highest |
| **Federated identity** | CI/CD, Kubernetes | High |

Client secrets are simple strings registered with your app in Microsoft Entra ID. While they're the easiest credential type to set up, they also have significant security limitations:

- They can be accidentally exposed in source code, logs, or configuration files.
- They have an expiration date and must be manually rotated.
- They provide no cryptographic proof of the caller's identity beyond possession of the secret.

## Configure a client secret in appsettings.json

To configure a client secret, add a `ClientCredentials` array to the `AzureAd` section of your `appsettings.json` file:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "YOUR_TENANT_ID",
    "ClientId": "YOUR_CLIENT_ID",
    "ClientCredentials": [
      {
        "SourceType": "ClientSecret",
        "ClientSecret": "YOUR_SECRET_VALUE"
      }
    ]
  }
}
```

The `ClientCredentials` array supports multiple entries. Microsoft.Identity.Web tries each credential in order until one succeeds, which is useful for secret rotation scenarios.

Warning

Never commit actual secret values to source control. The `YOUR_SECRET_VALUE` placeholder in the preceding example must be replaced with a reference to a secure store, as described in the following sections.

## Store secrets for development

This section describes how to keep secret values out of your source code during local development.

### .NET user secrets

The recommended approach for storing secrets during local development is the [Secret Manager tool](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets). User Secrets stores sensitive data outside your project tree, which prevents accidental commits to source control.

1. Initialize User Secrets for your project:

   ```dotnetcli
   dotnet user-secrets init
   ```

2. Set the client secret value:

   ```dotnetcli
   dotnet user-secrets set "AzureAd:ClientCredentials:0:ClientSecret" "your-secret-value"
   ```

3. Verify the secret was stored:

   ```dotnetcli
   dotnet user-secrets list
   ```

User Secrets are automatically loaded in the `Development` environment when you use `WebApplication.CreateBuilder()` or `Host.CreateDefaultBuilder()`.

Your `appsettings.json` should contain the structure without the actual secret value:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "YOUR_TENANT_ID",
    "ClientId": "YOUR_CLIENT_ID",
    "ClientCredentials": [
      {
        "SourceType": "ClientSecret"
      }
    ]
  }
}
```

### Environment variables

You can also use environment variables to provide the client secret. .NET configuration automatically maps environment variables that use the `__` \(double underscore\) separator to the configuration hierarchy. Set the variable for your shell:

- [PowerShell](#tabpanel_1_powershell)
- [Bash](#tabpanel_1_bash)

```powershell
$env:AzureAd__ClientCredentials__0__ClientSecret = "your-secret-value"
```

```bash
export AzureAd__ClientCredentials__0__ClientSecret="your-secret-value"
```

Environment variables take precedence over values in `appsettings.json`, so the secret value in your configuration file can be empty or omitted.

## Store secrets for higher environments

For staging, QA, or any shared environment, use Azure Key Vault as a configuration source. This approach keeps secrets out of configuration files and environment variables while providing auditing, access policies, and automatic rotation capabilities.

### Add Azure Key Vault as a configuration source

1. Install the required NuGet package:

   ```dotnetcli
   dotnet add package Azure.Extensions.AspNetCore.Configuration.Secrets
   ```

2. Store the client secret in Azure Key Vault with a name that maps to the configuration path. Use `--` \(double dash\) as the separator:

   ```azurecli
   az keyvault secret set \
     --vault-name "your-keyvault-name" \
     --name "AzureAd--ClientCredentials--0--ClientSecret" \
     --value "your-secret-value"
   ```

3. Add Key Vault as a configuration source in `Program.cs`. The following code registers Key Vault so its secrets are available through the standard configuration API:

   ```csharp
   var builder = WebApplication.CreateBuilder(args);

   builder.Configuration.AddAzureKeyVault(
       new Uri("https://your-keyvault-name.vault.azure.net/"),
       new DefaultAzureCredential());
   ```

The Key Vault secret name `AzureAd--ClientCredentials--0--ClientSecret` maps automatically to the `AzureAd:ClientCredentials:0:ClientSecret` configuration path.

Tip

Even when using Key Vault to store a client secret, consider whether your production workload would be better served by certificates or managed identities. Key Vault is useful for shared development or staging environments, but production applications should use stronger credential types.

## Create a client secret in the Azure portal

Follow these steps to register a client secret for your application in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Navigate to **Identity** > **Applications** > **App registrations**.
3. Select your application from the list.
4. In the left menu, select **Certificates & secrets**.
5. Select the **Client secrets** tab.
6. Select **New client secret**.
7. In the **Add a client secret** pane:

   - Enter a **Description** for the secret \(for example, "Development secret"\).
   - Select an **Expires** duration. Available options include 180 days, 365 days, 730 days, or a custom date.
   - Select **Add**.

8. **Copy the secret value immediately.** The value is only shown once and can't be retrieved after you navigate away from the page.

Important

Record the secret value in a secure location immediately after creation. Microsoft Entra ID only displays the value at creation time. If you lose the value, you must create a new secret.

## Manage secret expiration and rotation

Client secrets have a maximum lifetime and expire on the date specified during creation. Plan for secret rotation to avoid application outages.

### Monitor expiration

- Check the **Expires** column in the **Certificates & secrets** page of your app registration.
- Set up [Microsoft Entra recommendations](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/recommendation-renew-expiring-application-credential) to receive alerts before credentials expire.

### Rotation strategy

Use the `ClientCredentials` array to support zero-downtime rotation:

1. Create a new client secret in the Azure portal.
2. Add the new secret as an additional entry in the `ClientCredentials` array. Place the new secret first so it's tried before the old one:

   ```json
   {
     "AzureAd": {
       "ClientCredentials": [
         {
           "SourceType": "ClientSecret",
           "ClientSecret": "[NEW_SECRET_REFERENCE]"
         },
         {
           "SourceType": "ClientSecret",
           "ClientSecret": "[OLD_SECRET_REFERENCE]"
         }
       ]
     }
   }
   ```

3. Deploy the updated configuration. Microsoft.Identity.Web tries the first credential and falls back to the second if the first fails.
4. After confirming the new secret works, remove the old secret from both the configuration and the Azure portal.

## Migrate to production credentials

Before deploying to production, migrate from client secrets to a more secure credential type:

### Certificate-based authentication

Certificates provide cryptographic proof of identity and are the recommended credential type for production. The following configuration retrieves a certificate from Key Vault:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://your-keyvault-name.vault.azure.net",
        "KeyVaultCertificateName": "your-certificate-name"
      }
    ]
  }
}
```

For detailed steps, see [Use certificates with Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificates).

### Managed identity \(certificateless\)

For applications hosted in Azure, managed identities eliminate the need to manage credentials entirely. The following configuration uses a user-assigned managed identity:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity",
        "ManagedIdentityClientId": "YOUR_MANAGED_IDENTITY_CLIENT_ID"
      }
    ]
  }
}
```

For detailed steps, see [Certificateless authentication with Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificateless).

### Migration checklist

- \[ \] Generate or provision the new credential \(certificate or managed identity\).
- \[ \] Update your application configuration to use the new credential type.
- \[ \] Test the new credential in a staging environment.
- \[ \] Deploy to production.
- \[ \] Remove the old client secret from the Azure portal.
- \[ \] Verify the application functions correctly without the old secret.

## Avoid common security mistakes

Review the following anti-patterns and their recommended alternatives when working with client secrets:

| Anti-pattern | Risk | Recommendation |
| --- | --- | --- |
| Hard-coding secrets in source code | Secret exposed in version control | Use User Secrets, environment variables, or Key Vault |
| Committing `appsettings.Development.json` with secrets | Secret exposed to anyone with repository access | Add the file to `.gitignore` and use User Secrets instead |
| Sharing secrets across environments | Compromised dev secret exposes production | Use unique secrets per environment |
| Using secrets in production | Higher risk of credential theft | Migrate to certificates or managed identities |
| Creating secrets with no expiration plan | Application outage when secret expires | Set expiration reminders and implement rotation |
| Logging secret values | Secret exposed in log files | Never log credential values; log only the credential source type |
| Storing secrets in plain-text files on servers | Secret exposed to anyone with server access | Use environment variables or Key Vault |

## Troubleshoot common errors

This section covers frequent errors you might encounter when configuring client secrets.

### Invalid client secret

**Error:** `AADSTS7000215: Invalid client secret provided.`

**Possible causes:**

- The secret value was copied incorrectly. Secret values can contain special characters that get truncated during copy/paste operations.
- The secret was created for a different app registration than the one configured in `ClientId`.
- The configuration path is incorrect, and the secret value isn't being read by the application.

**Resolution:**

1. Create a new client secret in the Azure portal and carefully copy the full value.
2. Verify the `ClientId` and `TenantId` in your configuration match the app registration where the secret was created.
3. Add a breakpoint or log statement to verify the configuration is loaded correctly:

   ```csharp
   // For debugging only — remove before committing
   var config = builder.Configuration.GetSection("AzureAd:ClientCredentials:0:ClientSecret").Value;
   Console.WriteLine($"Secret loaded: {!string.IsNullOrEmpty(config)}");
   ```

### Expired client secret

**Error:** `AADSTS7000222: The provided client secret keys for app '{app-id}' are expired.`

**Resolution:**

1. Navigate to the app registration in the Microsoft Entra admin center.
2. Check the expiration date under **Certificates & secrets** > **Client secrets**.
3. Create a new secret and update your application configuration.
4. Delete the expired secret from the portal.

### Secret not found in configuration

**Symptom:** The application throws a `NullReferenceException` or fails to authenticate because the secret value is `null`.

**Possible causes:**

- User Secrets aren't initialized for the project.
- The environment variable name doesn't match the expected configuration path.
- Key Vault isn't configured as a configuration source.
- The application is running in a non-Development environment where User Secrets aren't loaded.

**Resolution:**

1. Verify User Secrets are initialized by checking for a `UserSecretsId` in your `.csproj` file.
2. Verify the secret is set by running `dotnet user-secrets list`.
3. Check that the configuration path matches exactly: `AzureAd:ClientCredentials:0:ClientSecret`.
4. If running outside the Development environment, ensure the appropriate configuration source \(environment variable or Key Vault\) is available.

## Related content

- [Certificates with Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificates)
- [Certificateless authentication](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificateless)
- [Token cache overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview)
- [Safe storage of app secrets in development in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets)
- [Azure Key Vault configuration provider in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/security/key-vault-configuration)
