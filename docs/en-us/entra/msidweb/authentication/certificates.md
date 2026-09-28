<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificates -->
<!-- Sitemap-Last-Modified: 2026-04-19 -->

# Use certificates with Microsoft.Identity.Web

Microsoft.Identity.Web supports certificate-based authentication as a secure alternative to client secrets for confidential client applications. Certificates use asymmetric cryptography, so only the private key holder can authenticate.

In this article, you configure certificate credentials from various sources, register them with your app, and manage them in production.

### Why use certificates?

| Factor | Client Secret | Certificate |
| --- | --- | --- |
| **Security** | Shared secret \(symmetric\) | Asymmetric key pair |
| **Rotation** | Requires app redeployment or config change | Can be automated via Key Vault |
| **Exposure risk** | Secret in config can be leaked | Private key stays in secure storage |
| **Compliance** | May not meet enterprise policies | Meets most enterprise security requirements |
| **Recommended for** | Development, prototyping | Production workloads |

Important

Microsoft recommends certificates over client secrets for production applications. For the highest security posture, use [certificateless authentication](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificateless) \(Managed Identity or Workload Identity Federation\) when your hosting environment supports it.

### How it works

1. You generate or obtain an X.509 certificate with a private key.
2. You register the certificate's **public key** \(or thumbprint\) with your Microsoft Entra app registration.
3. At runtime, Microsoft.Identity.Web loads the certificate \(including the private key\) from your configured source.
4. The library uses the private key to sign a client assertion, which it sends to Microsoft Entra ID to obtain tokens.

### Certificate sources

Microsoft.Identity.Web supports loading certificates from multiple sources:

| Source Type | `SourceType` Value | Best For |
| --- | --- | --- |
| Azure Key Vault | `KeyVault` | Production \(recommended\) |
| Certificate Store | `StoreWithThumbprint` or `StoreWithDistinguishedName` | Windows servers, on-premises |
| File path | `Path` | Development, containerized apps |
| Base64-encoded string | `Base64Encoded` | Kubernetes secrets, CI/CD pipelines |

You configure certificate credentials in the `ClientCertificates` array within your `AzureAd` \(or `AzureAdB2C`\) configuration section. You can specify multiple certificates for rotation scenarios — Microsoft.Identity.Web uses the first valid certificate it finds.

---

## From Azure Key Vault \(recommended\)

Azure Key Vault is the recommended source for certificates in production. It provides centralized management, access control, auditing, and automatic rotation capabilities.

### Configuration

Add the certificate configuration to your `appsettings.json`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",

    "ClientCertificates": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://your-keyvault-name.vault.azure.net",
        "KeyVaultCertificateName": "your-certificate-name"
      }
    ]
  }
}
```

| Property | Description |
| --- | --- |
| `SourceType` | Must be `"KeyVault"`. |
| `KeyVaultUrl` | The URI of your Azure Key Vault \(for example, `https://myapp-kv.vault.azure.net`\). |
| `KeyVaultCertificateName` | The name of the certificate as stored in Key Vault. |

### Set up Key Vault access policies

Your application's identity must have permission to read certificates from the Key Vault. How you grant this depends on whether you use the vault access policy model or Azure role-based access control \(RBAC\).

#### Option 1: Vault access policy

```azurecli
az keyvault set-policy \
  --name your-keyvault-name \
  --object-id <app-or-managed-identity-object-id> \
  --certificate-permissions get list \
  --secret-permissions get
```

Note

The `--secret-permissions get` permission is required because Azure Key Vault stores the private key as a secret linked to the certificate. Microsoft.Identity.Web needs access to both the certificate and its private key.

#### Option 2: Azure RBAC

Assign the **Key Vault Certificate User** role to your application's identity:

```azurecli
az role assignment create \
  --role "Key Vault Certificate User" \
  --assignee <app-or-managed-identity-object-id> \
  --scope /subscriptions/<sub-id>/resourceGroups/<rg>/providers/Microsoft.KeyVault/vaults/<vault-name>
```

### Use Managed Identity to access Key Vault

When your app runs in Azure \(App Service, Azure Functions, Azure Kubernetes Service, VMs\), use Managed Identity to authenticate to Key Vault. This eliminates the need for any credentials to access the vault itself.

#### System-assigned Managed Identity

If your app has a system-assigned Managed Identity enabled, Microsoft.Identity.Web automatically uses `DefaultAzureCredential` to authenticate to Key Vault. No extra configuration is needed beyond the `ClientCertificates` entry:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",

    "ClientCertificates": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://your-keyvault-name.vault.azure.net",
        "KeyVaultCertificateName": "your-certificate-name"
      }
    ]
  }
}
```

#### User-assigned Managed Identity

For a user-assigned Managed Identity, specify the `ManagedIdentityClientId` on the Key Vault certificate descriptor:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",

    "ClientCertificates": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://your-keyvault-name.vault.azure.net",
        "KeyVaultCertificateName": "your-certificate-name",
        "ManagedIdentityClientId": "user-assigned-managed-identity-client-id"
      }
    ]
  }
}
```

Tip

When running locally during development, `DefaultAzureCredential` falls back to your Azure CLI or Visual Studio credentials. Make sure you're signed in with `az login` and that your developer account has the appropriate Key Vault permissions.

---

## From certificate store \(Windows only\)

On Windows, you can load certificates from the Windows Certificate Store. This is common for on-premises or IIS-hosted deployments.

### By thumbprint

Use `StoreWithThumbprint` to identify the certificate by its SHA-1 thumbprint:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",

    "ClientCertificates": [
      {
        "SourceType": "StoreWithThumbprint",
        "CertificateStorePath": "CurrentUser/My",
        "CertificateThumbprint": "A1B2C3D4E5F6A1B2C3D4E5F6A1B2C3D4E5F6A1B2"
      }
    ]
  }
}
```

| Property | Description |
| --- | --- |
| `SourceType` | Must be `"StoreWithThumbprint"`. |
| `CertificateStorePath` | The certificate store location. Common values: `"CurrentUser/My"`, `"LocalMachine/My"`. |
| `CertificateThumbprint` | The SHA-1 thumbprint of the certificate \(40 hex characters\). |

### By distinguished name

Use `StoreWithDistinguishedName` to identify the certificate by its subject name:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",

    "ClientCertificates": [
      {
        "SourceType": "StoreWithDistinguishedName",
        "CertificateStorePath": "CurrentUser/My",
        "CertificateDistinguishedName": "CN=MyAppCertificate"
      }
    ]
  }
}
```

| Property | Description |
| --- | --- |
| `SourceType` | Must be `"StoreWithDistinguishedName"`. |
| `CertificateStorePath` | The certificate store location. Common values: `"CurrentUser/My"`, `"LocalMachine/My"`. |
| `CertificateDistinguishedName` | The subject distinguished name of the certificate \(for example, `"CN=MyAppCertificate"`\). |

### Certificate store locations

The following table lists common certificate store paths and the permissions required to access them:

| Path | Description | Permissions required |
| --- | --- | --- |
| `CurrentUser/My` | Current user's personal store | User-level access |
| `LocalMachine/My` | Machine-wide personal store | Administrator access |
| `LocalMachine/Root` | Trusted root CAs | Administrator access |
| `CurrentUser/Root` | Current user trusted root CAs | User-level access |

Note

When hosting in IIS, the application pool identity must have read access to the private key of the certificate. You can grant this using the **Manage Private Keys** option in the Certificates MMC snap-in.

---

## From file path

You can load a certificate directly from a `.pfx` \(PKCS#12\) file on disk.

Warning

Storing certificate files on disk with passwords in configuration is **not recommended for production**. Use this approach only for local development or in environments where the file system is secured \(for example, mounted secrets in containers\).

### Configuration

Add the certificate file path and password to your `appsettings.json`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",

    "ClientCertificates": [
      {
        "SourceType": "Path",
        "CertificateDiskPath": "/path/to/certificate.pfx",
        "CertificatePassword": "your-certificate-password"
      }
    ]
  }
}
```

| Property | Description |
| --- | --- |
| `SourceType` | Must be `"Path"`. |
| `CertificateDiskPath` | Absolute or relative path to the `.pfx` file. |
| `CertificatePassword` | Password for the `.pfx` file. If the certificate has no password, omit this property or set it to an empty string. |

Tip

To avoid storing the password in plain text in `appsettings.json`, reference it from an environment variable or a secrets manager:

**Using .NET User Secrets \(development\):**

```bash
dotnet user-secrets set "AzureAd:ClientCertificates:0:CertificatePassword" "your-password"
```

**Using an environment variable:**

```bash
export AzureAd__ClientCertificates__0__CertificatePassword="your-password"
```

---

## From Base64-encoded value

You can provide the certificate as a Base64-encoded string. This approach is useful when you inject certificates through environment variables, Kubernetes secrets, or CI/CD pipeline variables.

### Configuration

Add the Base64-encoded certificate value to your `appsettings.json`:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",

    "ClientCertificates": [
      {
        "SourceType": "Base64Encoded",
        "Base64EncodedValue": "MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4Egg..."
      }
    ]
  }
}
```

| Property | Description |
| --- | --- |
| `SourceType` | Must be `"Base64Encoded"`. |
| `Base64EncodedValue` | The full certificate \(including private key\) encoded as a Base64 string. |

### Generate the Base64 value

Convert a `.pfx` file to a Base64 string:

**PowerShell:**

```powershell
$certBytes = [System.IO.File]::ReadAllBytes("path/to/certificate.pfx")
$base64 = [System.Convert]::ToBase64String($certBytes)
$base64 | Set-Clipboard  # Copies to clipboard
```

**Bash:**

```bash
base64 -w 0 path/to/certificate.pfx
```

### Use with Kubernetes secrets

Store the Base64-encoded certificate in a Kubernetes secret and map it to an environment variable:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-cert-secret
type: Opaque
data:
  AzureAd__ClientCertificates__0__Base64EncodedValue: <base64-encoded-pfx>
```

Reference the secret in your deployment:

```yaml
env:
  - name: AzureAd__ClientCertificates__0__SourceType
    value: "Base64Encoded"
  - name: AzureAd__ClientCertificates__0__Base64EncodedValue
    valueFrom:
      secretKeyRef:
        name: app-cert-secret
        key: AzureAd__ClientCertificates__0__Base64EncodedValue
```

### Use in CI/CD pipelines

In Azure DevOps or GitHub Actions, store the Base64-encoded certificate as a secret variable, then set it as an environment variable at runtime.

**GitHub Actions example:**

```yaml
env:
  AzureAd__ClientCertificates__0__SourceType: "Base64Encoded"
  AzureAd__ClientCertificates__0__Base64EncodedValue: ${{ secrets.APP_CERTIFICATE_BASE64 }}
```

**Azure DevOps example:**

```yaml
variables:
  AzureAd__ClientCertificates__0__SourceType: "Base64Encoded"
  AzureAd__ClientCertificates__0__Base64EncodedValue: $(AppCertificateBase64)
```

Important

Even though the certificate is Base64-encoded, it contains the private key and must be treated as a secret. Always use secret variables in CI/CD pipelines — never commit Base64-encoded certificates to source control.

---

## Configure certificates in C# code

In addition to JSON configuration, you can configure certificate credentials programmatically using the `CredentialDescription` class from `Microsoft.Identity.Abstractions`.

### Helper methods

The `CredentialDescription` class provides static helper methods for each certificate source type:

```csharp
using Microsoft.Identity.Abstractions;

// From Azure Key Vault
var kvCredential = CredentialDescription.FromKeyVault(
    "https://your-keyvault-name.vault.azure.net",
    "your-certificate-name");

// From certificate store (by thumbprint)
var thumbprintCredential = CredentialDescription.FromCertificateStore(
    "CurrentUser/My",
    thumbprint: "A1B2C3D4E5F6A1B2C3D4E5F6A1B2C3D4E5F6A1B2");

// From certificate store (by distinguished name)
var dnCredential = CredentialDescription.FromCertificateStore(
    "CurrentUser/My",
    distinguishedName: "CN=MyAppCertificate");

// From file path
var pathCredential = CredentialDescription.FromCertificatePath(
    "/path/to/certificate.pfx",
    "your-certificate-password");

// From Base64-encoded string
var base64Credential = CredentialDescription.FromBase64String(
    "MIIKcQIBAzCCCi0GCSqGSIb3DQEHAaCCCh4Egg...");
```

### Use in ASP.NET Core

Pass the credential descriptions directly when configuring authentication:

```csharp
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(options =>
    {
        options.Instance = "https://login.microsoftonline.com/";
        options.TenantId = "your-tenant-id";
        options.ClientId = "your-client-id";
        options.ClientCredentials = new[]
        {
            CredentialDescription.FromKeyVault(
                "https://your-keyvault-name.vault.azure.net",
                "your-certificate-name")
        };
    });
```

Tip

The helper methods are equivalent to setting properties on a `CredentialDescription` object manually. They provide a more concise syntax when you configure credentials in code rather than through `appsettings.json`.

---

## Create a self-signed certificate for development

For local development and testing, you can create a self-signed certificate. Don't use self-signed certificates in production.

### Using PowerShell \(Windows\)

Run the following commands to create a self-signed certificate, export it, and display the thumbprint:

```powershell
$cert = New-SelfSignedCertificate `
  -Subject "CN=MyDevCertificate" `
  -CertStoreLocation "Cert:\CurrentUser\My" `
  -KeyExportPolicy Exportable `
  -KeySpec Signature `
  -KeyLength 2048 `
  -KeyAlgorithm RSA `
  -HashAlgorithm SHA256 `
  -NotAfter (Get-Date).AddYears(2)

# Export the .pfx file (with private key)
$password = ConvertTo-SecureString -String "YourPassword123!" -Force -AsPlainText
Export-PfxCertificate -Cert $cert -FilePath ".\MyDevCertificate.pfx" -Password $password

# Export the .cer file (public key only — for app registration)
Export-Certificate -Cert $cert -FilePath ".\MyDevCertificate.cer"

# Display the thumbprint
Write-Host "Thumbprint: $($cert.Thumbprint)"
```

### Using OpenSSL \(cross-platform\)

Run the following commands to generate a certificate, package it as a `.pfx` file, and display the thumbprint:

```bash
# Generate a self-signed certificate and private key
openssl req -x509 -newkey rsa:2048 \
  -keyout key.pem -out cert.pem \
  -days 730 -nodes \
  -subj "/CN=MyDevCertificate"

# Package into a .pfx file
openssl pkcs12 -export \
  -out MyDevCertificate.pfx \
  -inkey key.pem -in cert.pem \
  -passout pass:YourPassword123!

# Get the thumbprint
openssl x509 -in cert.pem -noout -fingerprint -sha1
```

### Using .NET CLI

Export a development HTTPS certificate as a `.pfx` file:

```bash
dotnet dev-certs https --export-path ./MyDevCertificate.pfx --password YourPassword123!
```

Note

The `dotnet dev-certs` command generates an HTTPS development certificate. While it can be used for testing certificate loading, it's primarily intended for local HTTPS and may not be suitable for all authentication testing scenarios.

---

## Register the certificate in Microsoft Entra ID

After you create or obtain a certificate, you must register its public key with your app registration in Microsoft Entra ID.

### Using the Azure portal

1. Go to the [Azure portal](https://portal.azure.com) and navigate to **Microsoft Entra ID** > **App registrations**.
2. Select your application.
3. Select **Certificates & secrets** > **Certificates** > **Upload certificate**.
4. Upload the `.cer` or `.pem` file containing the **public key only**. Don't upload the `.pfx` file, which contains the private key.
5. Note the **Thumbprint** value displayed after upload — you may need it for configuration.

### Using Azure CLI

```azurecli
az ad app credential reset \
  --id <application-client-id> \
  --cert @/path/to/certificate.pem \
  --append
```

The `--append` flag adds the certificate without removing existing credentials.

### Using Microsoft Graph PowerShell

```powershell
$certData = [System.IO.File]::ReadAllBytes(".\MyDevCertificate.cer")
$base64Cert = [System.Convert]::ToBase64String($certData)

$keyCredential = @{
    type = "AsymmetricX509Cert"
    usage = "Verify"
    key = [System.Convert]::FromBase64String($base64Cert)
    displayName = "MyAppCertificate"
}

Update-MgApplication -ApplicationId <app-object-id> -KeyCredentials @($keyCredential)
```

Important

Only upload the **public key** \(`.cer` or `.pem`\) to the app registration. Never upload the `.pfx` file, which contains the private key. The private key must remain securely stored and accessible only to your application.

---

## Certificate rotation

Certificate rotation replaces an expiring certificate with a new one before it expires, ensuring uninterrupted service.

### Strategy: Overlapping certificates

The recommended approach uses overlapping validity periods:

1. **Generate a new certificate** before the current one expires \(for example, 30–60 days in advance\).
2. **Register the new certificate** in your Microsoft Entra app registration alongside the existing one. Microsoft Entra ID accepts tokens signed by any registered certificate.
3. **Deploy the new certificate** to your application's certificate source \(Key Vault, certificate store, and so on\).
4. **Update configuration** \(if necessary\) to point to the new certificate.
5. **Remove the old certificate** from the app registration after confirming all instances use the new one.

### Multiple certificates in configuration

Microsoft.Identity.Web supports specifying multiple certificates. The library tries them in order and uses the first valid certificate:

```json
{
  "AzureAd": {
    "ClientCertificates": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://your-keyvault.vault.azure.net",
        "KeyVaultCertificateName": "new-cert-2026"
      },
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://your-keyvault.vault.azure.net",
        "KeyVaultCertificateName": "current-cert-2025"
      }
    ]
  }
}
```

### Automatic rotation with Azure Key Vault

Azure Key Vault supports automatic certificate renewal. When you enable auto-rotation:

1. Key Vault generates a new certificate version before expiry.
2. Microsoft.Identity.Web picks up the latest version automatically \(on next certificate fetch\).
3. The old certificate version remains valid until it expires.

To configure auto-rotation in Key Vault:

```azurecli
az keyvault certificate set-attributes \
  --vault-name your-keyvault-name \
  --name your-certificate-name \
  --policy @rotation-policy.json
```

Tip

For applications with long-running processes, consider implementing a periodic certificate refresh. Microsoft.Identity.Web caches the certificate in memory. If the certificate is rotated in Key Vault, the application picks up the new certificate the next time it needs to create a new MSAL confidential client application instance.

---

## Troubleshoot certificate errors

This section lists common error messages and their solutions.

### Common errors

#### Certificate not found

**Error message:**

```text
System.Security.Cryptography.CryptographicException: The certificate cannot be found.
```

**Possible causes and solutions:**

| Cause | Solution |
| --- | --- |
| Incorrect thumbprint | Verify the thumbprint in your configuration matches the installed certificate. Remove any hidden characters \(spaces, invisible Unicode\). |
| Wrong certificate store | Confirm `CertificateStorePath` matches where the certificate is installed \(`CurrentUser/My` vs `LocalMachine/My`\). |
| Certificate not installed | Import the certificate into the correct store using `certmgr.msc` \(CurrentUser\) or `certlm.msc` \(LocalMachine\). |
| Key Vault name mismatch | Verify `KeyVaultUrl` and `KeyVaultCertificateName` are correct. |
| File not found | Confirm `CertificateDiskPath` points to an existing `.pfx` file and the application has read access. |

#### Access denied to Key Vault

**Error message:**

```text
Azure.RequestFailedException: The user, group or application '...' does not have certificates get permission on key vault '...'
```

**Solutions:**

- Verify access policies grant `get` permission for both **certificates** and **secrets**.
- If using Azure RBAC, ensure the identity has the **Key Vault Certificate User** role.
- For Managed Identity, confirm the identity is enabled and the correct object ID is used in the policy.

#### Certificate private key not accessible

**Error message:**

```text
System.Security.Cryptography.CryptographicException: Keyset does not exist.
```

**Solutions:**

- On Windows/IIS, ensure the application pool identity has **read** access to the private key. Use the Certificates MMC snap-in to grant access via **Manage Private Keys**.
- On Linux, verify the `.pfx` file has appropriate file permissions \(`chmod 600`\).
- Ensure the certificate was exported with the private key \(`Export-PfxCertificate` or `openssl pkcs12 -export`\).

#### Certificate expired

**Error message:**

```text
AADSTS700027: Client assertion contains an invalid signature. The key was expired.
```

**Solutions:**

- Check the certificate's validity period: `openssl x509 -in cert.pem -noout -dates`.
- Generate a new certificate and update both the app registration and your application's configuration.
- Implement certificate rotation to prevent future expiration issues. See [Certificate rotation](#certificate-rotation).

#### Wrong certificate password

**Error message:**

```text
System.Security.Cryptography.CryptographicException: The specified network password is not correct.
```

**Solutions:**

- Verify `CertificatePassword` matches the password used when exporting the `.pfx` file.
- If using environment variables, check for encoding issues \(trailing newlines, special characters\).
- Re-export the certificate with a known password.

### Diagnostic checklist

Use this checklist when certificate authentication isn't working:

- \[ \] **Certificate validity** — Is the certificate within its validity period? Check `NotBefore` and `NotAfter` dates.
- \[ \] **App registration** — Is the certificate's public key uploaded to the correct app registration?
- \[ \] **Thumbprint match** — Does the thumbprint in your configuration match the certificate in the app registration?
- \[ \] **Private key access** — Can the application process read the certificate's private key?
- \[ \] **Key Vault permissions** — For Key Vault sources, does the identity have both `certificates/get` and `secrets/get` permissions?
- \[ \] **Configuration section** — Is the certificate configuration under the correct section \(`AzureAd` or `AzureAdB2C`\)?
- \[ \] **NuGet packages** — Is `Microsoft.Identity.Web` up to date? Older versions may lack support for certain certificate source types.

### Enable logging

To get detailed diagnostic information, enable MSAL logging:

```csharp
builder.Services.AddMicrosoftIdentityWebAppAuthentication(builder.Configuration, "AzureAd")
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddInMemoryTokenCaches();

builder.Logging.AddFilter("Microsoft.Identity", LogLevel.Debug);
```

Review the logs for messages about certificate loading, client assertion creation, and token acquisition.

---

## Related content

- [Credentials overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/credentials-overview)
- [Certificateless authentication](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificateless) — Managed Identity and Workload Identity Federation
- [Client secrets](https://learn.microsoft.com/en-us/entra/msidweb/authentication/client-secrets) — alternative credential type for confidential apps
- [Token decryption](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-decryption) — using certificates for token decryption
- [Logging and diagnostics](https://learn.microsoft.com/en-us/entra/msidweb/advanced/logging)
