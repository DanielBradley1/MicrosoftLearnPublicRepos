<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/managed-identity -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Scenario: Using Managed Identity

Use Microsoft Entra Workload ID to authenticate pods in Azure Kubernetes Service \(AKS\) to the Microsoft Entra ID Auth SDK \(sidecar\) without storing credentials. The SDK automatically acquires tokens using your pod's managed identity, eliminating the need for client secrets or certificates, keeping your application secure.

Important

For AKS, Microsoft Entra Workload ID uses **file-based token projection** with the `SignedAssertionFilePath` credential type. The workload identity webhook automatically projects the token to `/var/run/secrets/azure/tokens/azure-identity-token` in your pod. This is different from classic managed identity on VMs or App Services, which uses the `SignedAssertionFromManagedIdentity` credential type.

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- **Azure Kubernetes Service \(AKS\) cluster** with OIDC issuer and workload identity enabled. See [Quickstart: Deploy an AKS cluster](https://learn.microsoft.com/en-us/azure/aks/learn/quick-kubernetes-deploy-cli).
- **Microsoft Entra ID Auth SDK \(sidecar\)** container image available and ready to deploy. See [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation) for setup instructions.
- **Appropriate permissions in Microsoft Entra ID** - Your account must have permissions to create and manage managed identities, create federated identity credentials, and grant application permissions.
- **kubectl access** to your AKS cluster for deploying pods and creating Kubernetes resources.

## Setup steps

Follow these steps to configure Azure Managed Identity with the Microsoft Entra ID Auth SDK \(sidecar\):

### 1. Enable Workload Identity on AKS

To enable workload identity, create or update your AKS cluster with OIDC issuer and workload identity support:

```bash
# Create or update AKS cluster with workload identity
az aks create \
  --resource-group myResourceGroup \
  --name myAKSCluster \
  --enable-oidc-issuer \
  --enable-workload-identity

# Get OIDC issuer URL
export AKS_OIDC_ISSUER=$(az aks show \
  --resource-group myResourceGroup \
  --name myAKSCluster \
  --query "oidcIssuerProfile.issuerUrl" -o tsv)
```

### 2. Create Managed Identity

Next, you need to create a managed identity in Azure that your AKS pods will use to authenticate to the Microsoft Entra ID Auth SDK \(sidecar\):

```bash
# Create managed identity
az identity create \
  --resource-group myResourceGroup \
  --name myapp-identity

# Get identity details
export IDENTITY_CLIENT_ID=$(az identity show \
  --resource-group myResourceGroup \
  --name myapp-identity \
  --query clientId -o tsv)

export IDENTITY_OBJECT_ID=$(az identity show \
  --resource-group myResourceGroup \
  --name myapp-identity \
  --query principalId -o tsv)
```

### 3. Grant permissions

Grant the managed identity the necessary API permissions to access downstream APIs via the Microsoft Entra ID Auth SDK \(sidecar\):

```bash
# Grant Microsoft Graph permissions
az ad app permission add \
  --id $IDENTITY_CLIENT_ID \
  --api 00000003-0000-0000-c000-000000000000 \
  --api-permissions e1fe6dd8-ba31-4d61-89e7-88639da4683d=Scope  # User.Read

# Grant admin consent
az ad app permission admin-consent --id $IDENTITY_CLIENT_ID
```

### 4. Create Federated Identity credential

Create a federated identity credential to link the AKS workload identity with the managed identity:

```bash
# Create federated credential for Kubernetes service account
az identity federated-credential create \
  --name myapp-federated-identity \
  --identity-name myapp-identity \
  --resource-group myResourceGroup \
  --issuer $AKS_OIDC_ISSUER \
  --subject system:serviceaccount:default:myapp-sa
```

### 5. Create Kubernetes service account

Finally, create a Kubernetes service account annotated with the managed identity client ID:

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: myapp-sa
  namespace: default
  annotations:
    azure.workload.identity/client-id: "<MANAGED_IDENTITY_CLIENT_ID>"
```

Once created, you can apply the service account configuration with kubectl:

```bash
kubectl apply -f serviceaccount.yaml
```

## Deployment configuration

Deploy the Microsoft Entra ID Auth SDK \(sidecar\) alongside your application in a Kubernetes pod. The SDK automatically uses workload identity when configured:

### Complete pod configuration

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
  namespace: default
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
        azure.workload.identity/use: "true"  # Required for workload identity
    spec:
      serviceAccountName: myapp-sa
      containers:
      # Application container
      - name: app
        image: myregistry/myapp:latest
        ports:
        - containerPort: 8080
        env:
        - name: SIDECAR_URL
          value: "http://localhost:5000"
        resources:
          requests:
            memory: "256Mi"
            cpu: "250m"
          limits:
            memory: "512Mi"
            cpu: "500m"
      
      # SDK container
      - name: sidecar
        image: mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0
        ports:
        - containerPort: 5000
        env:
        # Microsoft Entra ID Configuration
        - name: AzureAd__Instance
          value: "https://login.microsoftonline.com/"
        - name: AzureAd__TenantId
          value: "common"  # Or specific tenant ID
        - name: AzureAd__ClientId
          value: "<MANAGED_IDENTITY_CLIENT_ID>"
        
        # Client Credentials - Use SignedAssertionFilePath for workload identity
        - name: AzureAd__ClientCredentials__0__SourceType
          value: "SignedAssertionFilePath"
        
        # Downstream API Configuration
        - name: DownstreamApis__Graph__BaseUrl
          value: "https://graph.microsoft.com/v1.0"
        - name: DownstreamApis__Graph__Scopes
          value: "User.Read Mail.Read"
        
        # Logging
        - name: Logging__LogLevel__Default
          value: "Information"
        - name: Logging__LogLevel__Microsoft.Identity.Web
          value: "Information"
        
        resources:
          requests:
            memory: "128Mi"
            cpu: "100m"
          limits:
            memory: "256Mi"
            cpu: "250m"
        
        livenessProbe:
          httpGet:
            path: /healthz
            port: 5000
          initialDelaySeconds: 10
          periodSeconds: 10
        
        readinessProbe:
          httpGet:
            path: /healthz
            port: 5000
          initialDelaySeconds: 5
          periodSeconds: 5
```

### How Workload Identity token projection works

When you configure a pod with the Azure Workload Identity label \(`azure.workload.identity/use: "true"`\) and a properly annotated service account, the Azure Workload Identity webhook automatically:

1. **Injects environment variables** into the pod:

   - `AZURE_CLIENT_ID` - The managed identity client ID from the service account annotation
   - `AZURE_TENANT_ID` - The tenant ID
   - `AZURE_FEDERATED_TOKEN_FILE` - Path to the projected token file \(`/var/run/secrets/azure/tokens/azure-identity-token`\)

2. **Projects the token file** as a volume mount at `/var/run/secrets/azure/tokens/azure-identity-token`
3. **Automatically refreshes** the token before it expires

The SDK uses the `SignedAssertionFilePath` credential type to read the token from this projected file location. This approach is specific to containerized workload identity and differs from classic managed identity on VMs or App Services.

## Verification

Verify that workload identity is properly configured and that the Microsoft Entra ID Auth SDK \(sidecar\) can acquire tokens by using the following steps:

### Test workload identity

Verify pod labels and service account configuration using kubectl commands:

```bash
# Check pod labels
kubectl get pod -l app=myapp -o yaml | grep -A 5 "labels:"

# Verify service account
kubectl get pod -l app=myapp -o yaml | grep serviceAccountName

# Check SDK logs
kubectl logs -l app=myapp -c sidecar

# Test token acquisition
kubectl exec -it $(kubectl get pod -l app=myapp -o name | head -1) -c app -- \
  curl -H "Authorization: Bearer <test-token>" \
  http://localhost:5000/AuthorizationHeader/Graph
```

### Verify environment variables

Check that Azure workload identity environment variables are correctly set in the pod:

```bash
# Check identity environment variables in pod
kubectl exec -it $(kubectl get pod -l app=myapp -o name | head -1) -c sidecar -- env | grep AZURE

# You should see:
# AZURE_CLIENT_ID=<managed-identity-client-id>
# AZURE_TENANT_ID=<tenant-id>
# AZURE_FEDERATED_TOKEN_FILE=/var/run/secrets/azure/tokens/azure-identity-token
```

## Application code

Because the Microsoft Entra ID Auth SDK \(sidecar\) uses the pod's managed identity to authenticate to Microsoft Entra ID, your application doesn't manage any client secrets or certificates. The application still forwards the incoming user token to the SDK so that on-behalf-of \(OBO\) flows can target the correct user, but no credential-handling code is required:

```typescript
// TypeScript example
async function getUserProfile(incomingToken: string) {
  const sidecarUrl = process.env.SIDECAR_URL!;

  const response = await fetch(
    `${sidecarUrl}/DownstreamApi/Graph?optionsOverride.RelativePath=me`,
    {
      method: 'POST',
      headers: {
        'Authorization': incomingToken
      }
    }
  );

  const result = await response.json();
  return JSON.parse(result.content);
}
```

## Multiple environments

Manage different authentication approaches across development and production environments:

### Development

Use client secret for local development - ensure you store secrets securely, and do not commit them to source control:

```yaml
# dev-secrets.yaml (local only, not committed)
apiVersion: v1
kind: Secret
metadata:
  name: sidecar-secrets-dev
type: Opaque
stringData:
  AzureAd__ClientCredentials__0__SourceType: "ClientSecret"
  AzureAd__ClientCredentials__0__ClientSecret: "<dev-client-secret>"
```

### Production

Use workload identity in production for secure, credential-free authentication:

```yaml
# prod-serviceaccount.yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: myapp-sa-prod
  annotations:
    azure.workload.identity/client-id: "<prod-managed-identity-client-id>"
```

## Troubleshooting

Diagnose and resolve common issues with workload identity and the Microsoft Entra ID Auth SDK \(sidecar\):

### Pod fails to start

Check pod events and logs to identify startup failures:

```bash
# Check pod events
kubectl describe pod -l app=myapp

# Check SDK logs
kubectl logs -l app=myapp -c sidecar
```

Common issues:

- Missing service account annotation with the managed identity client ID
- Missing pod label `azure.workload.identity/use: "true"`
- Incorrect or mismatched client ID in service account annotation

### Token acquisition fails

```bash
# Check logs for AADSTS errors
kubectl logs -l app=myapp -c sidecar | grep AADSTS
```

Common issues:

- Federated credential OIDC issuer URL does not match cluster's issuer URL exactly
- Subject pattern mismatch \(should be `system:serviceaccount:<namespace>:<service-account>`\)
- Managed identity lacks required permissions or admin consent not granted
- Service account not properly labeled or annotated

### Environment variables not set

Verify the workload identity webhook is configured and pods are properly mutated:

```bash
# Verify workload identity webhook is running
kubectl get pods -n kube-system | grep azure-workload-identity-webhook

# Check pod mutation
kubectl get pod -l app=myapp -o yaml | grep -A 10 "env:"
```

## Best practices

Follow these practices for security and operational excellence with managed identity:

- **Separate Identities per Environment**: Use different managed identities for development, staging, and production to limit blast radius if any identity is compromised.
- **Apply Least Privilege**: Grant only required permissions to each managed identity and regularly audit to revoke unnecessary access.
- **Enable Diagnostic Logging**: Configure Microsoft Entra audit logs and SDK diagnostic logging to monitor identity usage and detect suspicious patterns.
- **Review Permissions Regularly**: Periodically validate that granted permissions remain necessary for your application.
- **Maintain Documentation**: Document all permissions granted to each managed identity and their business justification.
- **Test in Staging**: Verify workload identity configuration in a staging environment before production deployment.
- **Apply Proper Labels**: Use consistent Kubernetes labels \(`azure.workload.identity/use: "true"`\) for managed identity pods to simplify operations.

Managed identity eliminates the need to manage client secrets or certificates, automatically renews tokens, provides complete audit trails in Microsoft Entra ID, integrates seamlessly with Azure RBAC, and enhances your security posture by reducing credential exposure risks.

## Comparison with other methods

Compare managed identity with alternative authentication approaches:

| Method | Security | Complexity | Maintenance |
| --- | --- | --- | --- |
| **Workload identity** | High — short-lived federated tokens with no shared secrets to leak or rotate. | Moderate — one-time setup of OIDC issuer, federated credential, and pod labels. | Low — tokens are issued and rotated automatically by the platform. |
| Certificate \(Key Vault\) | High — private key never leaves Key Vault and access is auditable. | Moderate — requires Key Vault provisioning and access policies. | Moderate — certificates must be renewed and access policies maintained. |
| Certificate \(Kubernetes Secret\) | Medium — private key is stored in the cluster and depends on RBAC and encryption-at-rest. | Low — uses standard Kubernetes Secret resources. | High — certificates must be renewed and redistributed manually. |
| Client secret | Low — long-lived shared secret that's vulnerable to leakage. | Low — only requires storing the secret value. | High — secrets must be rotated frequently and distributed securely. |

Workload identity offers the highest security rating because of token-based authentication without shared secrets, requires moderate setup effort, and needs minimal ongoing maintenance compared to the other approaches.

## Related content

- [Call a downstream API](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/call-downstream-api)
- [Long-running on-behalf-of](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/long-running-on-behalf)
- [Security](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)
- [Configuration](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
