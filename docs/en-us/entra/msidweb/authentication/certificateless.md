<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificateless -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Configure certificateless authentication with Microsoft.Identity.Web

This article shows you how to configure certificateless authentication so your application authenticates with Microsoft Entra ID without managing certificates or client secrets. Your app uses a Federated Identity Credential \(FIC\) backed by an Azure Managed Identity to obtain tokens, which eliminates credential rotation, reduces secret sprawl, and simplifies Azure deployments.

Microsoft.Identity.Web supports certificateless authentication through the `SignedAssertionFromManagedIdentity` credential source type, available in version 2.12.0 and later.

---

## Understand certificateless authentication

This section explains how certificateless authentication works and when to use it.

Traditionally, confidential client applications prove their identity to Microsoft Entra ID by presenting a client secret or a certificate. Both approaches require you to manage credential lifecycle—rotating secrets before they expire, renewing certificates, and securely storing them.

Federated Identity Credentials \(FIC\) change this model. With FIC, you configure a trust relationship between your app registration and a Managed Identity. When your application needs to authenticate:

1. Microsoft.Identity.Web requests a token from the Managed Identity endpoint on the Azure host.
2. The library uses the Managed Identity token as a signed assertion to authenticate with Microsoft Entra ID.
3. Microsoft Entra ID validates the signed assertion against the federated credential configuration on the app registration.
4. Microsoft Entra ID issues an access token for the requested resource.

The result is a fully credential-free deployment where no secrets or certificates exist in your configuration, code, or environment variables.

### Choose the right authentication approach

The following table helps you decide when certificateless authentication is the right choice.

| Scenario | Recommended approach |
| --- | --- |
| App runs on Azure and you want zero credential management | Certificateless with FIC |
| App runs on Azure but needs to support on-premises fallback | Certificate-based credentials with FIC as primary |
| App runs outside Azure \(on-premises, other clouds\) | Certificates or client secrets |
| Development and testing on local machines | Client secrets or certificate from a local store |

---

## Prerequisites

Verify that you have the following resources and tools before you start:

- An **Azure subscription**. If you don't have one, [create a free account](https://azure.microsoft.com/free/).
- An **app registration** in Microsoft Entra ID with the required API permissions for your scenario.
- A **Managed Identity** in Azure—either system-assigned on your compute resource or a standalone user-assigned Managed Identity.
- **Microsoft.Identity.Web** version 2.12.0 or later installed in your project.
- An Azure compute resource that supports Managed Identity, such as Azure App Service, Azure Kubernetes Service \(AKS\), Azure Container Apps, or Azure Virtual Machines.

---

## Step 1: Create or identify a Managed Identity

You can use either a system-assigned or user-assigned Managed Identity. If you haven't created one yet, follow the instructions for your scenario.

### Option A: Use a system-assigned Managed Identity

System-assigned Managed Identities are tied to the lifecycle of an Azure resource. When you enable a system-assigned identity on a resource like an App Service, Azure creates an identity automatically.

1. In the [Azure portal](https://portal.azure.com), navigate to your compute resource \(for example, your App Service\).
2. Select **Identity** from the left navigation menu.
3. On the **System assigned** tab, set **Status** to **On**.
4. Select **Save** and confirm the action.
5. After the identity is created, copy the **Object \(principal\) ID**. You need this value when configuring the federated credential.

### Option B: Create a user-assigned Managed Identity

User-assigned Managed Identities are standalone Azure resources that you can assign to one or more compute resources.

1. In the [Azure portal](https://portal.azure.com), search for **Managed Identities** and select it.
2. Select **Create**.
3. Choose your **Subscription**, **Resource group**, **Region**, and enter a **Name** for the identity.
4. Select **Review + create**, then **Create**.
5. After deployment completes, open the new Managed Identity resource.
6. Copy the **Client ID** from the **Overview** page. You need this value for your application configuration.

---

## Step 2: Configure a Federated Identity credential in the Azure portal

A Federated Identity Credential establishes a trust relationship between your app registration and the Managed Identity. Follow these steps to create one:

1. In the [Azure portal](https://portal.azure.com), go to **Microsoft Entra ID** > **App registrations**.
2. Select the app registration that your application uses.
3. In the left navigation menu, select **Certificates & secrets**.
4. Select the **Federated credentials** tab.
5. Select **Add credential**.
6. Under **Federated credential scenario**, select **Customer managed keys** or **Other issuer** \(the available options depend on your portal version\).
7. Configure the following fields:
   | Field | Value |
   | --- | --- |
   | **Issuer** | `https://login.microsoftonline.com/{tenant-id}/v2.0` — Replace `{tenant-id}` with your Microsoft Entra tenant ID. |
   | **Subject identifier** | The **Object \(principal\) ID** of the Managed Identity. For system-assigned, find this on the resource's Identity page. For user-assigned, find this on the Managed Identity's Overview page under **Principal ID**. |
   | **Name** | A descriptive name, for example `fic-managed-identity-prod`. |
   | **Audience** | `api://AzureADTokenExchange` \(the default value\). |
8. Select **Add**.

Important

The **Subject identifier** must exactly match the **Object \(principal\) ID** of the Managed Identity. A mismatch causes authentication to fail with an `AADSTS70021` error.

### Configure a Federated Identity credential with Azure CLI

Alternatively, create the federated credential with the Azure CLI. The following command creates a credential on your app registration:

```azurecli
az ad app federated-credential create \
    --id <app-object-id> \
    --parameters '{
        "name": "fic-managed-identity-prod",
        "issuer": "https://login.microsoftonline.com/<tenant-id>/v2.0",
        "subject": "<managed-identity-principal-id>",
        "audiences": ["api://AzureADTokenExchange"],
        "description": "FIC for production managed identity"
    }'
```

### Issuer URLs by Azure service

The issuer URL in the federated credential depends on the Azure service that hosts your application:

| Azure service | Issuer URL |
| --- | --- |
| Azure App Service / Azure Functions | `https://login.microsoftonline.com/{tenant-id}/v2.0` |
| Azure Container Apps | `https://login.microsoftonline.com/{tenant-id}/v2.0` |
| Azure Kubernetes Service \(AKS\) | The OIDC issuer URL for your cluster \(retrieve with `az aks show --query oidcIssuerProfile.issuerUrl`\) |
| Azure Virtual Machines | `https://login.microsoftonline.com/{tenant-id}/v2.0` |

### Subject identifier format

The format of the subject identifier depends on the Managed Identity type:

**System-assigned Managed Identity** — Use the Object \(principal\) ID from the resource's **Identity** page. This is a GUID value, for example `a1b2c3d4-e5f6-7890-abcd-ef1234567890`.

**User-assigned Managed Identity** — Use the **Principal ID** \(also called Object ID\) from the Managed Identity resource's **Overview** page. This is also a GUID value.

Note

For AKS with workload identity, the subject identifier uses a different format: `system:serviceaccount:{namespace}:{service-account-name}`. This value must match the Kubernetes service account that your pod uses.

---

## Step 3: Configure your application

### Update appsettings.json

Add the `ClientCredentials` section to your `AzureAd` configuration. Set the `SourceType` to `SignedAssertionFromManagedIdentity`:

#### For user-assigned Managed Identity

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "YOUR_TENANT_ID",
    "ClientId": "YOUR_CLIENT_ID",
    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity",
        "ManagedIdentityClientId": "USER_ASSIGNED_MSI_CLIENT_ID"
      }
    ]
  }
}
```

Replace the following placeholders:

| Placeholder | Description |
| --- | --- |
| `YOUR_TENANT_ID` | Your Microsoft Entra tenant ID. |
| `YOUR_CLIENT_ID` | The Application \(client\) ID of your app registration. |
| `USER_ASSIGNED_MSI_CLIENT_ID` | The Client ID of the user-assigned Managed Identity \(from the identity's Overview page\). |

#### For system-assigned Managed Identity

When you use a system-assigned Managed Identity, omit the `ManagedIdentityClientId` property. Microsoft.Identity.Web automatically uses the system-assigned identity of the host:

```json
{
  "AzureAd": {
    "Instance": "https://login.microsoftonline.com/",
    "TenantId": "YOUR_TENANT_ID",
    "ClientId": "YOUR_CLIENT_ID",
    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity"
      }
    ]
  }
}
```

### Register services in Program.cs

No special code changes are required in your startup configuration. The standard Microsoft.Identity.Web registration methods read the `ClientCredentials` section automatically.

The following example registers authentication for a web app that signs in users and calls downstream APIs:

```csharp
// For a web app that signs in users and calls downstream APIs
builder.Services.AddAuthentication(OpenIdConnectDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApp(builder.Configuration.GetSection("AzureAd"))
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddInMemoryTokenCaches();
```

The following example registers authentication for a web API that calls downstream APIs:

```csharp
// For a web API that calls downstream APIs
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"))
    .EnableTokenAcquisitionToCallDownstreamApi()
    .AddInMemoryTokenCaches();
```

The following example registers authentication for a daemon application with no user interaction:

```csharp
// For a daemon application (no user interaction)
builder.Services.AddAuthentication()
    .AddMicrosoftIdentityWebApi(builder.Configuration.GetSection("AzureAd"));

builder.Services.AddTokenAcquisition()
    .AddInMemoryTokenCaches();
```

Microsoft.Identity.Web detects the `SignedAssertionFromManagedIdentity` source type and handles the token exchange transparently.

---

## Compare system-assigned and user-assigned Managed Identity

Choose the Managed Identity type that best fits your architecture. The following sections outline the tradeoffs.

### System-assigned Managed Identity

A system-assigned identity is created and deleted automatically with the Azure resource it belongs to.

**Advantages:**

- No separate resource to manage—identity lifecycle matches the compute resource.
- Simpler setup for single-resource deployments.
- No `ManagedIdentityClientId` required in configuration.

**Considerations:**

- You can't share the identity across multiple resources.
- If you delete and recreate the resource, the identity changes—you must update the Federated Identity Credential.

**Best for:** Single-instance deployments where one compute resource maps to one app registration.

### User-assigned Managed Identity

A user-assigned identity is a standalone Azure resource with its own lifecycle.

**Advantages:**

- Share a single identity across multiple compute resources \(for example, multiple App Service instances in different regions\).
- Identity persists independently of compute resource lifecycle.
- Pre-create and pre-configure before deploying the compute resource.

**Considerations:**

- An additional Azure resource to manage.
- You must specify the `ManagedIdentityClientId` in configuration.

**Best for:** Multi-instance or multi-region deployments, blue-green deployment patterns, and scenarios where compute resources are frequently recreated.

---

## Deploy to Azure compute services

After you configure your application, deploy it to an Azure compute service that supports Managed Identity.

### Azure App Service

1. Enable Managed Identity on your App Service \(see [Step 1](#step-1-create-or-identify-a-managed-identity)\).
2. Deploy your application to the App Service using your preferred method \(Visual Studio, Azure CLI, GitHub Actions\).
3. Ensure the `AzureAd` section in your deployed configuration matches the settings in [Step 3](#step-3-configure-your-application).
4. If you use a user-assigned Managed Identity, assign it to the App Service:

   ```azurecli
   az webapp identity assign \
     --resource-group <resource-group> \
     --name <app-service-name> \
     --identities <managed-identity-resource-id>
   ```

5. Restart the App Service to pick up the identity assignment.

### Azure Kubernetes service \(AKS\)

For AKS, use workload identity to associate a Kubernetes service account with the Managed Identity. Complete the following steps:

1. Enable the workload identity feature on your AKS cluster:

   ```azurecli
   az aks update \
     --resource-group <resource-group> \
     --name <aks-cluster-name> \
     --enable-oidc-issuer \
     --enable-workload-identity
   ```

2. Create a Kubernetes service account annotated with the Managed Identity client ID:

   ```yaml
   apiVersion: v1
   kind: ServiceAccount
   metadata:
     name: my-app-sa
     namespace: default
     annotations:
       azure.workload.identity/client-id: "<USER_ASSIGNED_MSI_CLIENT_ID>"
   ```

3. Create a federated credential linking the AKS OIDC issuer to the Managed Identity.
4. Configure your pod to use the service account:

   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: my-app
     namespace: default
     labels:
       azure.workload.identity/use: "true"
   spec:
     serviceAccountName: my-app-sa
     containers:
       - name: my-app
         image: <your-container-image>
   ```

5. Deploy the pod. The workload identity webhook injects the required environment variables for the Managed Identity token endpoint.

### Azure Container Apps

1. Create or update your Container App with a Managed Identity:

   ```azurecli
   az containerapp identity assign \
     --resource-group <resource-group> \
     --name <container-app-name> \
     --user-assigned <managed-identity-resource-id>
   ```

2. Deploy your container image with the appropriate `AzureAd` configuration.
3. The Managed Identity token endpoint is automatically available inside the container.

---

## Migrate from certificates to certificateless authentication

If your application currently uses certificate-based authentication, you can migrate to certificateless authentication with minimal configuration changes.

### Complete the migration steps

1. **Create a Managed Identity** for your Azure compute resource \(see [Step 1](#step-1-create-or-identify-a-managed-identity)\).
2. **Add a Federated Identity Credential** to your app registration \(see [Step 2](#step-2-configure-a-federated-identity-credential-in-the-azure-portal)\).
3. **Update your configuration** to add the `SignedAssertionFromManagedIdentity` credential. You can keep the existing certificate credential as a fallback during migration:

   ```json
   {
     "AzureAd": {
       "Instance": "https://login.microsoftonline.com/",
       "TenantId": "YOUR_TENANT_ID",
       "ClientId": "YOUR_CLIENT_ID",
       "ClientCredentials": [
         {
           "SourceType": "SignedAssertionFromManagedIdentity",
           "ManagedIdentityClientId": "USER_ASSIGNED_MSI_CLIENT_ID"
         },
         {
           "SourceType": "KeyVault",
           "KeyVaultUrl": "https://your-keyvault.vault.azure.net",
           "KeyVaultCertificateName": "your-cert-name"
         }
       ]
     }
   }
   ```


   Microsoft.Identity.Web tries credential sources in order. When running on Azure, the first credential \(`SignedAssertionFromManagedIdentity`\) succeeds. If it fails \(for example, during local development\), the library falls back to the certificate.

4. **Deploy and validate** in a staging environment before applying to production.
5. **Remove the certificate credential** from the configuration after you confirm that certificateless authentication works in production.
6. **Delete the certificate** from Azure Key Vault and the app registration when it's no longer needed.

### Compare before and after configuration

The following examples show the configuration change from certificate-based to certificateless authentication.

**Before \(certificate-based\):**

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "KeyVault",
        "KeyVaultUrl": "https://your-keyvault.vault.azure.net",
        "KeyVaultCertificateName": "your-cert-name"
      }
    ]
  }
}
```

**After \(certificateless\):**

```json
{
  "AzureAd": {
    "ClientCredentials": [
      {
        "SourceType": "SignedAssertionFromManagedIdentity",
        "ManagedIdentityClientId": "USER_ASSIGNED_MSI_CLIENT_ID"
      }
    ]
  }
}
```

---

## Troubleshoot common errors

Use the following guidance to diagnose and resolve issues with certificateless authentication.

### AADSTS70021: No matching federated identity record found

**Cause:** The subject identifier in the Federated Identity Credential doesn't match the Managed Identity's object \(principal\) ID.

**Resolution:**

1. In the Azure portal, navigate to the Managed Identity resource and copy the **Principal ID** \(also called Object ID\) from the **Overview** page.
2. Navigate to your app registration > **Certificates & secrets** > **Federated credentials**.
3. Verify the **Subject identifier** field matches the principal ID exactly.
4. If the values don't match, delete the credential and recreate it with the correct subject identifier.

### AADSTS700024: Client assertion is not within its valid time range

**Cause:** The Managed Identity token used as the signed assertion has expired or the system clock is skewed.

**Resolution:**

- Verify the system clock on your Azure resource is accurate.
- Restart the application to force a new Managed Identity token request.
- If you run in a container, ensure the container's clock is synchronized with the host.

### ManagedIdentityException: Managed Identity endpoint not available

**Cause:** The application can't reach the Azure Instance Metadata Service \(IMDS\) or the Managed Identity token endpoint.

**Resolution:**

- Confirm the application is running on an Azure compute resource that supports Managed Identity.
- Verify the Managed Identity is enabled and assigned to the compute resource.
- For AKS, verify the workload identity webhook is running and the pod has the correct service account annotation.
- For local development, this error is expected. Use a fallback credential source \(see [Migration steps](#complete-the-migration-steps)\).

### AADSTS700016: Application not found in the directory

**Cause:** The `ClientId` in your configuration doesn't match a valid app registration in the specified tenant.

**Resolution:**

- Verify the `ClientId` matches the **Application \(client\) ID** of your app registration.
- Verify the `TenantId` matches the tenant where the app is registered.

### Enable debug logging

**Cause:** The credential source order or configuration mismatch might cause the library to skip the FIC credential.

**Resolution:**

1. Enable logging in Microsoft.Identity.Web to see detailed token acquisition steps. The following code configures debug-level logging for the identity libraries:

   ```csharp
   builder.Services.AddLogging(logging =>
   {
       logging.AddConsole();
       logging.SetMinimumLevel(LogLevel.Debug);
       logging.AddFilter("Microsoft.Identity", LogLevel.Debug);
   });
   ```

2. Review the logs for messages about which credential source the library attempted and any errors returned.

### User-assigned Managed Identity not picked up

**Cause:** When multiple user-assigned Managed Identities are assigned to a compute resource, the library might use the wrong one if `ManagedIdentityClientId` isn't specified.

**Resolution:**

- Always specify the `ManagedIdentityClientId` property when you use a user-assigned Managed Identity.
- Verify the client ID matches the identity you configured the Federated Identity Credential for.

---

## Review security benefits

Certificateless authentication with FIC provides significant security advantages over traditional credential-based approaches:

### No secrets to leak

Because no certificate files, PFX passwords, or client secrets exist in your configuration or deployment artifacts, there's nothing for an attacker to extract. Even if an attacker gains read access to your configuration files, they can't impersonate your application from outside Azure.

### No credential rotation

Managed Identity tokens are short-lived and automatically refreshed by the Azure platform. You don't need to implement rotation schedules, monitor expiration dates, or coordinate credential updates across deployments.

### Reduced attack surface

The Managed Identity token endpoint is only accessible from the specific Azure resource the identity is assigned to. An attacker can't use the credential from a different host, network, or cloud environment.

### Compliance simplification

Without long-lived credentials, you eliminate several categories of compliance concerns:

- No secrets stored in source control, environment variables, or configuration files.
- No key material to audit, rotate, or revoke.
- No certificate infrastructure \(CA, renewal processes\) to maintain.

### Defense in depth

Combine certificateless authentication with other Azure security features for layered protection:

- **Azure RBAC**: Control which identities can access which resources.
- **Conditional Access**: Apply policies based on identity risk, location, and device state.
- **Private endpoints**: Restrict network access to Azure resources.
- **Microsoft Defender for Cloud**: Monitor for suspicious authentication patterns.

---

## Related content

- [Credentials overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/credentials-overview)
- [Certificates](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificates)
- [Client secrets](https://learn.microsoft.com/en-us/entra/msidweb/authentication/client-secrets)
- [Azure Managed Identities documentation](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview)
- [Federated Identity Credentials documentation](https://learn.microsoft.com/en-us/graph/api/resources/federatedidentitycredentials-overview)
- [Microsoft.Identity.Web GitHub repository](https://github.com/AzureAD/microsoft-identity-web)
