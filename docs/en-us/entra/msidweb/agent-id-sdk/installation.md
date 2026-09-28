<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Installation guide: Deploy the Microsoft Entra ID Auth SDK \(sidecar\)

The Microsoft Entra ID Auth SDK \(sidecar\) is a ready-to-deploy containerized authentication service that streamlines secure token acquisition for your applications. This installation guide provides step-by-step instructions for deploying the SDK container across Kubernetes, Docker, and Azure environments, eliminating the need to embed sensitive credentials directly in your application code.

## Prerequisites

- Access to [Microsoft Artifact Registry](https://mcr.microsoft.com/)
- Container runtime \(Docker, Kubernetes, or container service\)
- Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com), configured for *Accounts in this organizational directory only*. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp) for more details. Record the following values from the application **Overview** page for later use:

  - Application \(client\) ID
  - Directory \(tenant\) ID

- Credentials for the application:

  - Client Secret or Certificate stored securely \(e.g., Azure Key Vault\)

- For Azure deployments: [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli) or access to [Azure portal](https://portal.azure.com/)

## Container image

The Microsoft Entra ID Auth SDK \(sidecar\) is distributed as a container image from the artifact registry

```text
mcr.microsoft.com/entra-sdk/auth-sidecar
```

Note

Inbound SHR PoP validation requires sidecar version `1.1.2-preview` or later.

## Deployment patterns

The Microsoft Entra ID Auth SDK \(sidecar\) is designed to run as a companion container alongside your application. This allows your application to offload token acquisition and management to the SDK via HTTP calls, and keeps sensitive credentials out of your application code. The following are common deployment patterns and should be adapted to your specific environment.

### Kubernetes pattern

Deploy the Microsoft Entra ID Auth SDK \(sidecar\) in the same pod as your application container for secure pod-local communication. This pattern ensures the authentication service runs alongside your app, enabling fast HTTP-based token acquisition while keeping credentials isolated from your application code:

```yaml
apiVersion: v1
kind: Pod
metadata:
  # Your application container
  name: myapp
spec:
  containers:
  - name: app
    image: myregistry/myapp:latest
    ports:
    - containerPort: 8080
    env:
    - name: SIDECAR_URL
      value: "http://localhost:5000"
  # Microsoft Entra ID Auth SDK (sidecar) container
  - name: sidecar
    image: mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0
    ports:
    - containerPort: 5000
    env:
    - name: AzureAd__TenantId
      value: "your-tenant-id"
    - name: AzureAd__ClientId
      value: "your-client-id"
    - name: AzureAd__ClientCredentials__0__SourceType
      value: "KeyVault"
    - name: AzureAd__ClientCredentials__0__KeyVaultUrl
      value: "https://your-keyvault.vault.azure.net"
    - name: AzureAd__ClientCredentials__0__KeyVaultCertificateName
      value: "your-cert-name"
```

### Kubernetes deployment

See [Kubernetes on Azure tutorial - Prepare an application for Azure Kubernetes Service \(AKS\)](https://learn.microsoft.com/en-us/azure/aks/tutorial-kubernetes-prepare-app?tabs=azure-cli) if you want to target Azure Kubernetes Services. This pattern uses a Deployment resource to manage application and Microsoft Entra ID Auth SDK \(sidecar\) containers, allowing for scaling and updates. The deployment also handles health checks and resource allocation, ensuring secure operation in production environments:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      serviceAccountName: myapp-sa
      containers:
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
      
      - name: sidecar
        image: mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0
        ports:
        - containerPort: 5000
        env:
        - name: AzureAd__TenantId
          valueFrom:
            configMapKeyRef:
              name: app-config
              key: tenant-id
        - name: AzureAd__ClientId
          valueFrom:
            configMapKeyRef:
              name: app-config
              key: client-id
        - name: AzureAd__Instance
          value: "https://login.microsoftonline.com/"
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

### Docker compose

When working in a Docker environment, you can use Docker Compose to define and run multi-container applications. The following example demonstrates how to set up the Microsoft Entra ID Auth SDK \(sidecar\) alongside your application container in a local development environment:

```yaml
version: '3.8'

services:
  app:
    image: myregistry/myapp:latest
    ports:
      - "8080:8080"
    environment:
      - AzureAd__TenantId=${TENANT_ID}
      - AzureAd__ClientId=${CLIENT_ID}
      - AzureAd__ClientCredentials__0__SourceType=ClientSecret
      - AzureAd__ClientCredentials__0__ClientSecret=${CLIENT_SECRET}
    networks:
      - app-network

networks:
  app-network:
    driver: bridge
```

## Azure Kubernetes service \(AKS\) with Managed Identity

When deploying to AKS, you can use [Azure Managed Identity](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/overview) to authenticate the Microsoft Entra ID Auth SDK \(sidecar\) without storing credentials in configuration. First you'll need to enable Microsoft Entra Workload ID on your AKS cluster and create a federated identity credential for your managed identity. Then configure the SDK to use the managed identity for authentication.

### Step 1: Create Managed Identity

Create a managed identity and assign it appropriate permissions

```bash
# Create managed identity
az identity create \
  --resource-group myResourceGroup \
  --name myapp-identity

# Get the identity details
IDENTITY_CLIENT_ID=$(az identity show \
  --resource-group myResourceGroup \
  --name myapp-identity \
  --query clientId -o tsv)

IDENTITY_OBJECT_ID=$(az identity show \
  --resource-group myResourceGroup \
  --name myapp-identity \
  --query principalId -o tsv)
```

### Step 2: Assign permissions

Grant the managed identity permissions to access downstream APIs:

```bash
# Example: Grant permission to call Microsoft Graph
az ad app permission add \
  --id $IDENTITY_CLIENT_ID \
  --api 00000003-0000-0000-c000-000000000000 \
  --api-permissions e1fe6dd8-ba31-4d61-89e7-88639da4683d=Scope
```

### Step 3: Configure Workload Identity

Create a service account with workload identity federation:

```bash
export AKS_OIDC_ISSUER=$(az aks show \
  --resource-group myResourceGroup \
  --name myAKSCluster \
  --query "oidcIssuerProfile.issuerUrl" -o tsv)

az identity federated-credential create \
  --name myapp-federated-identity \
  --identity-name myapp-identity \
  --resource-group myResourceGroup \
  --issuer $AKS_OIDC_ISSUER \
  --subject system:serviceaccount:default:myapp-sa
```

### Step 4: Deploy with Workload Identity

In the following deployment example, the Microsoft Entra ID Auth SDK \(sidecar\) is configured to use Microsoft Entra Workload ID for authentication using file-based token projection. The `SignedAssertionFilePath` credential type reads the token from the file projected by the workload identity webhook:

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: myapp-sa
  namespace: default
  annotations:
    azure.workload.identity/client-id: "<MANAGED_IDENTITY_CLIENT_ID>"

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-deployment
spec:
  template:
    metadata:
      labels:
        azure.workload.identity/use: "true"
    spec:
      serviceAccountName: myapp-sa
      containers:
      - name: app
        image: myregistry/myapp:latest
        env:
        - name: SIDECAR_URL
          value: "http://localhost:5000"
      
      - name: sidecar
        image: mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0
        ports:
        - containerPort: 5000
        env:
        - name: AzureAd__TenantId
          value: "your-tenant-id"
        - name: AzureAd__ClientId
          value: "<MANAGED_IDENTITY_CLIENT_ID>"
        
        # Workload Identity credentials - uses file-based token projection
        - name: AzureAd__ClientCredentials__0__SourceType
          value: "SignedAssertionFilePath"
```

**Note**: The workload identity webhook automatically projects the federated token to `/var/run/secrets/azure/tokens/azure-identity-token` or an environment variable when the pod has the required label and service account annotation.

## Network configuration

Correct network configuration is essential to ensure secure communication between the Microsoft Entra ID Auth SDK \(sidecar\) and external services while restricting unauthorized access. Proper configuration prevents security vulnerabilities and ensures reliable connectivity to Microsoft Entra ID endpoints. Use the following guidelines to configure network access for the SDK, depending on your deployment environment.

### Internal communication only

To configure the Microsoft Entra ID Auth SDK \(sidecar\) for internal pod-local communication only, set the endpoint URL in your application to point to `localhost` or `127.0.0.1`, depending on your environment:

```yaml
containers:
- name: sidecar
  env:
  - name: Kestrel__Endpoints__Http__Url
    value: "http://127.0.0.1:5000" # Same pod, localhost communication
```

Caution

Never expose the Microsoft Entra ID Auth SDK \(sidecar\) externally via LoadBalancer or Ingress. It should only be accessible from your application container.

### Network policies

To further restrict network access, consider implementing Kubernetes Network Policies to limit traffic to and from the SDK container:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: sidecar-network-policy
spec:
  podSelector:
    matchLabels:
      app: myapp
  policyTypes:
  - Ingress
  - Egress
  ingress:
  # No external ingress rules - only pod-local communication
  egress:
  - to:
    - namespaceSelector:
        matchLabels:
          name: kube-system
    ports:
    - protocol: TCP
      port: 53  # DNS
  - to:
    - podSelector: {}
  - to:
    # Allow outbound to Microsoft Entra ID
    ports:
    - protocol: TCP
      port: 443
```

## Health checks

The Microsoft Entra ID Auth SDK \(sidecar\) exposes a `/healthz` endpoint for liveness and readiness probes, ensuring the container is running safely. Configure your deployment to include these probes:

```yaml
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

## Resource requirements

The recommended resource allocations are as follows, but ensure to adjust based on token acquisition frequency, number of configured downstream APIs and cache size requirements:

| Resource Profile | Memory | CPU |
| --- | --- | --- |
| **Minimum** | 128Mi | 100m |
| **Recommended** | 256Mi | 250m |
| **High Traffic** | 512Mi | 500m |

## Scaling considerations

The Microsoft Entra ID Auth SDK \(sidecar\) is designed to scale with your application:

1. **Stateless Design**: Each SDK instance maintains its own token cache
2. **Horizontal Scaling**: Scale by adding more application pods \(each with its own SDK instance\)
3. **Cache Warming**: Consider implementing cache warming strategies for high-traffic scenarios

## Troubleshooting deployment

Common issues that you may encounter could be due to invalid configuration values, network connectivity to Microsoft Entra ID, or missing credentials or certificates. Ensure the managed identity or service principal has the correct application permissions, admin consent granted \(if required\), and correct role assignments.

The following are some common troubleshooting steps that can help resolve deployment issues:

### Container Won't start

Check container logs:

```bash
kubectl logs <pod-name> -c sidecar
```

### Health check failures

Verify the Microsoft Entra ID Auth SDK \(sidecar\) is responding:

```bash
kubectl exec <pod-name> -c sidecar -- curl http://localhost:5000/healthz
```

For more detailed steps on troubleshooting, refer to the [Troubleshooting guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/troubleshooting).

## Related content

- [Configuration Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
- [Endpoints Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/endpoints)
- [Security Best Practices](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)
- [Validate Authorization Header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/validate-authorization-header)
