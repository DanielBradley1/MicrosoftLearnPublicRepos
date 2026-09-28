<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/authentication/credentials-overview -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Credentials overview for Microsoft.Identity.Web

When your application authenticates with the Microsoft identity platform, it presents a credential to prove its identity. Microsoft.Identity.Web supports several credential types, each suited to different environments and security requirements.

This article helps you understand the available credential types, choose the right one for your scenario, and configure credentials in your application.

## Why credential choice matters

The credential your application uses directly affects its security posture, operational overhead, and deployment flexibility. A poorly chosen credential can expose secrets, require manual rotation, or limit where your application can run.

Microsoft.Identity.Web provides a unified configuration model that lets you:

- Specify multiple credentials with automatic fallback.
- Change credential types without modifying application code.
- Use different credentials per environment \(development, staging, production\).

## Supported credential types

Microsoft.Identity.Web supports three categories of credentials for confidential client applications:

### Certificateless credentials \(Federated Identity credentials + Managed Identity\)

Certificateless credentials use Azure Managed Identity combined with Federated Identity Credentials \(FIC\) to authenticate your application without managing any secrets or certificates. Azure handles the credential lifecycle entirely.

**How it works:** Your application uses its managed identity to obtain a token, which the Microsoft identity platform accepts as proof of the application's identity through a pre-configured federation trust.

**Best for:** Production workloads running on Azure.

[Learn more about certificateless authentication](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificateless)

### Certificates

Certificates provide strong, asymmetric key-based authentication. Your application proves its identity by signing an assertion with the certificate's private key. Microsoft.Identity.Web can load certificates from multiple sources:

- **Azure Key Vault** - Centralized, managed certificate storage with access policies.
- **Certificate Store** - Windows certificate store \(CurrentUser or LocalMachine\).
- **File path** - Certificate file on disk \(.pfx format\).
- **Base64-encoded** - Certificate embedded directly in configuration.

**Best for:** Production workloads where certificateless credentials aren't available, or hybrid environments.

[Learn more about certificate credentials](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificates)

### Client secrets

Client secrets are shared strings that your application presents to the Microsoft identity platform. They're the simplest credential type to configure but offer the weakest security.

**Best for:** Local development and testing only.

[Learn more about client secrets](https://learn.microsoft.com/en-us/entra/msidweb/authentication/client-secrets)

---

## Choose the right credential type

Use the following decision tree to determine which credential type is appropriate for your scenario.

```text
Is your application running on Azure?
├── Yes
│   ├── Can you use Managed Identity?
│   │   ├── Yes → Use certificateless credentials (recommended)
│   │   └── No → Use certificates from Azure Key Vault
└── No
    ├── Is this a production environment?
    │   ├── Yes → Use certificates (Key Vault, Certificate Store, or file path)
    │   └── No → Use client secrets for development/testing
```

### General guidance

Follow these principles when selecting a credential type:

- **Always prefer certificateless credentials** when your application runs on Azure. They eliminate credential management entirely.
- **Use certificates** when certificateless credentials aren't available. Store them in Azure Key Vault whenever possible.
- **Restrict client secrets to development environments.** Never use client secrets in production deployments.

---

## Compare credential types

The following table summarizes the key differences between credential types:

| Characteristic | Certificateless \(FIC + MI\) | Certificates | Client secrets |
| --- | --- | --- | --- |
| **Security level** | Highest | High | Low |
| **Secret exposure risk** | None - no secret to leak | Low - private key protected | High - string can be copied |
| **Rotation required** | No - Azure manages lifecycle | Yes - before certificate expiry | Yes - before secret expiry |
| **Rotation complexity** | None | Medium - update certificate, redeploy | Low - update string, redeploy |
| **Azure portal setup** | Managed Identity + FIC trust | Upload certificate to app registration | Generate secret in app registration |
| **Suitable environments** | Azure production | Any production environment | Development and testing only |
| **Infrastructure dependency** | Azure compute resource | Certificate store or Key Vault | None |
| **Compliance** | Meets zero-trust requirements | Meets most compliance frameworks | May not meet security policies |

---

## Configure credentials in appsettings.json

Microsoft.Identity.Web uses a `ClientCredentials` array in your configuration to specify one or more credentials. Each entry in the array includes a `SourceType` property that indicates where the credential comes from.

### Configuration structure

The following example shows a minimal configuration with a single certificateless credential:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",

    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity",
        "ManagedIdentityClientId": "user-assigned-managed-identity-client-id"
      }
    ]
  }
}
```

### SourceType values

The `SourceType` property corresponds to the `CredentialSource` enum and determines how Microsoft.Identity.Web loads the credential:

| SourceType value | Credential type | Description |
| --- | --- | --- |
| `SignedAssertionFromManagedIdentity` | Certificateless | Uses managed identity to obtain a signed assertion. Recommended for Azure production. |
| `KeyVault` | Certificate | Loads a certificate from Azure Key Vault by URI. |
| `StoreWithThumbprint` | Certificate | Loads a certificate from the Windows certificate store by thumbprint. |
| `StoreWithDistinguishedName` | Certificate | Loads a certificate from the Windows certificate store by subject distinguished name. |
| `Path` | Certificate | Loads a certificate from a .pfx file on disk. |
| `Base64Encoded` | Certificate | Loads a certificate from a Base64-encoded string in configuration. |
| `ClientSecret` | Client secret | Uses a client secret string. |
| `AutoDecryptKeys` | Token decryption | Automatically retrieves keys for decrypting encrypted tokens. |
| `SignedAssertionFilePath` | Federated | Reads a signed assertion from a file path \(for Kubernetes workload identity\). |

### Credential examples by type

The following examples show how to configure each credential type in `appsettings.json` and, where available, in C# code.

#### Certificateless \(managed identity\)

Use a user-assigned managed identity by specifying its client ID:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity",
        "ManagedIdentityClientId": "user-assigned-managed-identity-client-id"
      }
    ]
  }
}
```

For system-assigned managed identity, omit the `ManagedIdentityClientId` property:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity"
      }
    ]
  }
}
```

#### Certificate from Azure Key Vault

Load a certificate stored in Azure Key Vault by specifying the vault URL and certificate name:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://your-keyvault.vault.azure.net",
        "KeyVaultCertificateName": "your-certificate-name"
      }
    ]
  }
}
```

You can also use the `CredentialDescription` helper method in C#:

```csharp
var credential = CredentialDescription.FromKeyVault(
    "https://your-keyvault.vault.azure.net",
    "your-certificate-name");
```

#### Certificate from certificate store

Load a certificate from the Windows certificate store by thumbprint:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "StoreWithThumbprint",
        "CertificateThumbprint": "ABC123DEF456...",
        "CertificateStorePath": "CurrentUser/My"
      }
    ]
  }
}
```

You can also use a distinguished name, which simplifies certificate rotation because the new certificate is selected automatically:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "StoreWithDistinguishedName",
        "CertificateDistinguishedName": "CN=YourAppCertificate",
        "CertificateStorePath": "CurrentUser/My"
      }
    ]
  }
}
```

In C#, use the helper method:

```csharp
// By thumbprint
var credential = CredentialDescription.FromCertificateStore(
    "CurrentUser/My",
    thumbprint: "ABC123DEF456...");

// By distinguished name (recommended for rotation)
var credential = CredentialDescription.FromCertificateStore(
    "CurrentUser/My",
    distinguishedName: "CN=YourAppCertificate");
```

#### Certificate from file path

Load a certificate from a `.pfx` file on disk:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "Path",
        "CertificateDiskPath": "/var/certs/app-cert.pfx",
        "CertificatePassword": "certificate-password"
      }
    ]
  }
}
```

Warning

Avoid storing certificate passwords directly in `appsettings.json`. Use [ASP.NET Core Secret Manager](https://learn.microsoft.com/en-us/aspnet/core/security/app-secrets), environment variables, or Azure Key Vault for sensitive values.

#### Base64-encoded certificate

Embed a certificate directly in configuration as a Base64-encoded string:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "Base64Encoded",
        "Base64EncodedValue": "MIIKcQIBAzCCCi0..."
      }
    ]
  }
}
```

#### Client secret

Specify a client secret string for development and testing:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "ClientSecret",
        "ClientSecret": "your-client-secret"
      }
    ]
  }
}
```

Caution

Client secrets should only be used during development. Never commit secrets to source control or deploy them to production environments.

---

## Use multiple credentials with fallback

You can specify multiple credentials in the `ClientCredentials` array. Microsoft.Identity.Web tries each credential in order and falls back to the next one if the current one fails. This pattern is useful for applications that run in multiple environments.

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity",
        "ManagedIdentityClientId": "your-managed-identity-client-id"
      },
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://your-keyvault.vault.azure.net",
        "KeyVaultCertificateName": "your-certificate-name"
      },
      {
        "SourceType": "ClientSecret",
        "ClientSecret": "development-only-secret"
      }
    ]
  }
}
```

In this example:

1. The application first attempts certificateless authentication with managed identity \(works on Azure\).
2. If managed identity is unavailable, it falls back to a certificate from Key Vault.
3. As a last resort, it uses a client secret \(for local development\).

This approach lets you use the same configuration file across environments without code changes.

---

## Configure credentials in code

You can also configure credentials programmatically in `Program.cs` or `Startup.cs`:

```csharp
using Microsoft.Identity.Web;

builder.Services.AddMicrosoftIdentityWebAppAuthentication(builder.Configuration, "AzureAd")
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddDownstreamApi("MyApi", builder.Configuration.GetSection("MyApi"))
    .AddDistributedTokenCaches();

// Or configure credentials programmatically
builder.Services.Configure<MicrosoftIdentityOptions>(options =>
{
    options.ClientCredentials = new[]
    {
        new CredentialDescription
        {
            SourceType = CredentialSource.SignedAssertionFromManagedIdentity,
            ManagedIdentityClientId = "your-managed-identity-client-id"
        }
    };
});
```

---

## Token decryption credentials

Beyond client credentials for authentication, Microsoft.Identity.Web also supports credentials for token decryption. Use token decryption credentials when your application receives encrypted tokens and needs to decrypt them.

Token decryption credentials use the same `SourceType` values and configuration patterns as client credentials, but are specified in the `TokenDecryptionCredentials` array:

```json
{
  "AzureAd": {
    "TokenDecryptionCredentials": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://your-keyvault.vault.azure.net",
        "KeyVaultCertificateName": "token-decryption-cert"
      }
    ]
  }
}
```

[Learn more about token decryption](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-decryption)

---

## Best practices

Keep these recommendations in mind when configuring credentials for your application:

**Prefer certificateless credentials in production.** They eliminate secret exposure risk and remove rotation overhead. Use them whenever your application runs on Azure compute resources that support managed identity.

**Use credential fallback for portability.** Configure multiple credentials in priority order so your application works across development, staging, and production without code changes.

**Never use client secrets in production.** Client secrets can leak through logs, configuration files, or source control. Use certificates or certificateless credentials instead.

**Store sensitive values outside configuration files.** Use Azure Key Vault, environment variables, or the ASP.NET Core Secret Manager for certificate passwords and client secrets. Don't commit sensitive values to source control.

**Rotate certificates before they expire.** Monitor certificate expiration dates and establish a rotation process. Azure Key Vault can automate certificate renewal.

**Use Azure Key Vault for certificate storage.** Key Vault provides centralized management, access policies, audit logging, and automatic rotation for certificates.

## Related content

- [Certificateless authentication](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificateless)
- [Certificate credentials](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificates)
- [Token decryption](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-decryption)
- [Client secrets](https://learn.microsoft.com/en-us/entra/msidweb/authentication/client-secrets)
