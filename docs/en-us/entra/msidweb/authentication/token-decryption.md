<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-decryption -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Configure token decryption in Microsoft.Identity.Web

This article explains how to configure token decryption certificates in Microsoft.Identity.Web so your application can decrypt encrypted tokens from the Microsoft identity platform.

By default, the Microsoft identity platform issues tokens \(ID tokens, SAML tokens\) as signed but unencrypted JWTs. Any intermediary that intercepts a token can read its claims. For applications that handle sensitive claims or operate in strict compliance environments, the Microsoft identity platform supports **token encryption**. When enabled, the identity platform encrypts the token payload using a public key registered with your application. Only your application—which holds the corresponding private key—can decrypt and read the token.

### How token encryption works

1. You generate a certificate with a public/private key pair.
2. You upload the **public key** \(the `.cer` file\) to your app registration in Microsoft Entra ID.
3. When the Microsoft identity platform issues a token for your application, it encrypts the token using your public key.
4. Your application uses the **private key** to decrypt the token before processing claims.

The encryption uses a two-layer scheme: the token payload is encrypted with a symmetric content encryption key, which is wrapped \(encrypted\) using your public key. Microsoft Entra supports RSA-OAEP and RSA-OAEP-256 key-wrapping algorithms.

## Determine when to configure token decryption

Configure token decryption when your application meets one of the following conditions:

- **Receives encrypted SAML tokens** — Enterprise applications that use SAML-based single sign-on and require encrypted SAML assertions for compliance or regulatory reasons.
- **Receives encrypted ID tokens** — Web applications that opt in to ID token encryption to protect sensitive claims \(group memberships, custom claims\) from being read in transit.
- **Operates in high-security environments** — Applications in government, financial, or healthcare scenarios where token confidentiality is mandated by policy.

Note

Token encryption is optional. Most applications don't need it. Only enable token encryption if you have a specific requirement, because it adds operational complexity \(certificate management, rotation\) and makes troubleshooting more difficult.

## Meet the prerequisites

Before you configure token decryption, verify the following requirements:

- **An X.509 certificate with a private key** — You need a certificate in `.pfx` \(PKCS#12\) format or stored in a location accessible to your application \(Azure Key Vault, certificate store, or file system\). The private key is required to decrypt tokens.
- **App registration configured for token encryption** — Upload the certificate's public key to your app registration in Microsoft Entra ID. See [Register the decryption certificate](#register-the-decryption-certificate-in-microsoft-entra-id) later in this article.
- **Microsoft.Identity.Web 2.1.0 or later** — The `TokenDecryptionCredentials` configuration property is available in Microsoft.Identity.Web 2.1.0 and later.

---

## Configure token decryption in appsettings.json

Microsoft.Identity.Web uses the `TokenDecryptionCredentials` array in your `AzureAd` configuration section. This array follows the same credential description format as `ClientCredentials`, so you can load decryption certificates from Azure Key Vault, the certificate store, a file path, or a Base64-encoded string.

### Set up a basic configuration

The following example shows the minimum configuration to load a decryption certificate from Azure Key Vault:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "your-tenant-id",
    "ClientId": "your-client-id",
    "CallbackPath": "/signin-oidc",

    "TokenDecryptionCredentials": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://mykeyvault.vault.azure.net",
        "KeyVaultCertificateName": "MyCertificate"
      }
    ]
  }
}
```

No additional code is required. When Microsoft.Identity.Web detects the `TokenDecryptionCredentials` configuration, it automatically loads the specified certificate and registers it with the OpenID Connect authentication handler for token decryption.

---

## Choose a credential source

The `TokenDecryptionCredentials` array supports the same source types as `ClientCredentials`. The following table summarizes each option:

| SourceType | Description | Required properties |
| --- | --- | --- |
| **KeyVault** | Load the certificate from Azure Key Vault. Recommended for production. | `KeyVaultUrl`, `KeyVaultCertificateName` |
| **StoreWithThumbprint** | Load from the local certificate store by thumbprint. | `CertificateStorePath`, `CertificateThumbprint` |
| **StoreWithDistinguishedName** | Load from the local certificate store by subject distinguished name. | `CertificateStorePath`, `CertificateDistinguishedName` |
| **Path** | Load from a `.pfx` file on the file system. | `CertificateDiskPath`, `CertificatePassword` |
| **Base64Encoded** | Load from a Base64-encoded `.pfx` string \(useful for environment variables\). | `Base64EncodedValue` |

### Key Vault \(recommended for production\)

The following configuration loads a decryption certificate from Azure Key Vault:

```json
{
  "TokenDecryptionCredentials": [
    {
      "SourceType": "KeyVault",
      "KeyVaultUrl": "https://mykeyvault.vault.azure.net",
      "KeyVaultCertificateName": "TokenDecryptionCert"
    }
  ]
}
```

Your application's managed identity or service principal must have **Get** and **List** permissions on the Key Vault certificates.

### Certificate store \(Windows\)

The following configuration loads a certificate from the Windows certificate store by thumbprint:

```json
{
  "TokenDecryptionCredentials": [
    {
      "SourceType": "StoreWithThumbprint",
      "CertificateStorePath": "CurrentUser/My",
      "CertificateThumbprint": "A1B2C3D4E5F6..."
    }
  ]
}
```

### File path

The following configuration loads a certificate from a `.pfx` file on disk:

```json
{
  "TokenDecryptionCredentials": [
    {
      "SourceType": "Path",
      "CertificateDiskPath": "/var/ssl/private/decrypt-cert.pfx",
      "CertificatePassword": "your-certificate-password"
    }
  ]
}
```

Warning

Avoid storing certificate passwords in `appsettings.json` in production. Use environment variables, Azure Key Vault references, or a secrets manager instead.

### Base64-encoded

The following configuration loads a certificate from a Base64-encoded string:

```json
{
  "TokenDecryptionCredentials": [
    {
      "SourceType": "Base64Encoded",
      "Base64EncodedValue": "MIIJ..."
    }
  ]
}
```

This option is useful when you inject the certificate through an environment variable or CI/CD pipeline secret.

---

## Configure multiple decryption certificates

You can specify multiple certificates in the `TokenDecryptionCredentials` array. Microsoft.Identity.Web tries each certificate in order until one successfully decrypts the token. This capability is essential for **certificate rotation** \(see [Certificate rotation](#rotate-decryption-certificates)\).

```json
{
  "TokenDecryptionCredentials": [
    {
      "SourceType": "KeyVault",
      "KeyVaultUrl": "https://mykeyvault.vault.azure.net",
      "KeyVaultCertificateName": "TokenDecryptionCert-New"
    },
    {
      "SourceType": "KeyVault",
      "KeyVaultUrl": "https://mykeyvault.vault.azure.net",
      "KeyVaultCertificateName": "TokenDecryptionCert-Old"
    }
  ]
}
```

---

## Register the decryption certificate in Microsoft Entra ID

For the Microsoft identity platform to encrypt tokens for your application, you must upload the certificate's **public key** to your app registration:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Navigate to **Identity** > **Applications** > **App registrations** and select your application.
3. Select **Certificates & secrets** > **Certificates** > **Upload certificate**.
4. Upload the `.cer` file \(public key only\) of your decryption certificate.
5. After uploading, note the **Thumbprint** value — it must match the certificate your application uses.

### Enable token encryption for the application

After uploading the certificate, you must configure your application to receive encrypted tokens. This configuration is currently available through the Microsoft Graph API or PowerShell:

**Using Microsoft Graph PowerShell:**

```powershell
# Get the key credential ID of the uploaded certificate
$app = Get-MgApplication -Filter "appId eq 'your-client-id'"
$keyId = ($app.KeyCredentials | Where-Object { $_.DisplayName -eq "CN=TokenDecryptionCert" }).KeyId

# Set the token encryption key ID
Update-MgApplication -ApplicationId $app.Id -BodyParameter @{
    "tokenEncryptionKeyId" = $keyId
}
```

Important

The `tokenEncryptionKeyId` property on the application object identifies which uploaded certificate Microsoft Entra uses to encrypt tokens. Only one encryption key can be active at a time.

---

## Rotate decryption certificates

Certificate rotation for token decryption requires a careful, phased approach to avoid downtime:

### Rotation steps

1. **Generate a new certificate** — Create a new X.509 certificate with a private key.
2. **Add the new certificate to your application configuration** — Add the new certificate to the `TokenDecryptionCredentials` array alongside the existing certificate. Place the new certificate first in the array.
3. **Upload the new public key** — Upload the new certificate's `.cer` file to your app registration in Microsoft Entra.
4. **Deploy your application** — Deploy the updated configuration so your application can decrypt tokens with either certificate.
5. **Switch the active encryption key** — Update the `tokenEncryptionKeyId` on the application object to point to the new certificate's `keyId`.
6. **Verify** — Confirm that your application successfully decrypts tokens encrypted with the new certificate.
7. **Remove the old certificate** — After a grace period \(at least 24 hours to allow cached tokens to expire\), remove the old certificate from both your app registration and your application configuration.

### Configuration during rotation

During the rotation window, your `TokenDecryptionCredentials` should contain both certificates:

```json
{
  "TokenDecryptionCredentials": [
    {
      "SourceType": "KeyVault",
      "KeyVaultUrl": "https://mykeyvault.vault.azure.net",
      "KeyVaultCertificateName": "TokenDecryptionCert-2026"
    },
    {
      "SourceType": "KeyVault",
      "KeyVaultUrl": "https://mykeyvault.vault.azure.net",
      "KeyVaultCertificateName": "TokenDecryptionCert-2025"
    }
  ]
}
```

Tip

Automate certificate rotation by using Azure Key Vault's auto-rotation feature combined with Key Vault event notifications to trigger application redeployments.

---

## Troubleshoot token decryption

Use the following guidance to diagnose and resolve common token decryption issues.

### Token decryption failures

**Symptom:** Your application throws a `SecurityTokenDecryptionFailedException` or returns a 401/500 error when processing tokens.

**Common causes:**

| Cause | Solution |
| --- | --- |
| Certificate not found | Verify the certificate exists at the configured location \(Key Vault, store, or file path\). Check that your application has the required permissions to access it. |
| Wrong certificate | Verify that the certificate thumbprint in your application configuration matches the certificate uploaded to the app registration. |
| `tokenEncryptionKeyId` not set | Set the `tokenEncryptionKeyId` property on the application object in Microsoft Entra. Without this property, the identity platform doesn't encrypt tokens. |

### Missing private key

**Symptom:** `CryptographicException: The certificate key is not accessible` or `InvalidOperationException: Certificate does not have a private key`.

**Causes and solutions:**

- **Certificate exported without private key** — Re-export the certificate in `.pfx` format and ensure you include the private key during export.
- **Key Vault access policy** — When using Azure Key Vault, ensure your application's identity has the **Get** permission on both **Certificates** and **Secrets**. The private key is stored as a secret in Key Vault.
- **Certificate store permissions** — On Windows, verify that the application pool identity or service account has read access to the private key. Use the **Manage Private Keys** option in the certificate store MMC snap-in.

### Algorithm mismatch

**Symptom:** `SecurityTokenDecryptionFailedException` with a message indicating an unsupported algorithm.

**Causes and solutions:**

- **Unsupported key type** — Microsoft Entra supports RSA certificates for token encryption. Ensure your certificate uses an RSA key pair \(not EC/ECDSA\).
- **Key size too small** — Use a key size of at least 2048 bits. RSA keys smaller than 2048 bits might be rejected.
- **Algorithm not supported** — Microsoft Entra uses RSA-OAEP for key wrapping. Ensure your certificate and application infrastructure support this algorithm.

### Encrypted tokens not being issued

**Symptom:** Your application receives unencrypted tokens even though you configured token decryption.

**Causes and solutions:**

- **`tokenEncryptionKeyId` not configured** — You must explicitly set this property through Microsoft Graph. Uploading the certificate alone isn't sufficient.
- **Certificate expired in app registration** — Verify that the certificate uploaded to your app registration hasn't expired. Upload a new certificate if needed.
- **Access tokens aren't encrypted** — Token encryption applies to **ID tokens** and **SAML tokens** only. Access tokens from Microsoft Entra aren't encrypted with your certificate.

---

## Compare token decryption and client credentials

Token decryption credentials serve a different purpose from client credentials. Your application can use the same certificate for both, or use separate certificates.

The following example shows a configuration that uses the same Key Vault certificate for both authentication and token decryption:

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://mykeyvault.vault.azure.net",
        "KeyVaultCertificateName": "AppAuthCert"
      }
    ],
    "TokenDecryptionCredentials": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://mykeyvault.vault.azure.net",
        "KeyVaultCertificateName": "AppAuthCert"
      }
    ]
  }
}
```

Note

When you use the same certificate for both purposes, the certificate must have the `KeyEncipherment` key usage and use the `KeyExchange` key spec \(not `Signature`\). Certificates generated with `KeySpec = Signature` work for client credentials but fail for token decryption.

## Follow best practices

Apply these recommendations when you implement token decryption.

**Use Azure Key Vault** — Store decryption certificates in Key Vault for centralized management, access control, and audit logging.

**Plan for rotation** — Always have a rotation strategy before deploying token encryption. Include both the new and old certificates during the rotation window.

**Use RSA 2048-bit or larger keys** — Ensure your certificates use RSA keys of at least 2048 bits for adequate security.

**Monitor certificate expiration** — Set up alerts in Azure Key Vault or your monitoring system to notify you before certificates expire.

**Test in a staging environment** — Verify token encryption and decryption in a non-production environment before enabling it in production.

**Don't store private keys in source control** — Use Key Vault, environment variables, or a secrets manager for certificate storage.

**Don't remove the old certificate too early during rotation** — Keep both certificates active for at least 24 hours to allow cached tokens to expire.

**Don't enable token encryption without a decryption certificate configured** — Your application will fail to process tokens if it can't decrypt them.

## Related content

- [Credentials overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/credentials-overview)
- [Token cache overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview)
- [Authorization in web APIs](https://learn.microsoft.com/en-us/entra/msidweb/authentication/authorization)
- [Certificate credentials](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificates)
