<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# Security best practices: Hardening the Microsoft Entra ID Auth SDK \(sidecar\)

This guide provides comprehensive security configuration and hardening best practices for safely deploying and operating the Microsoft Entra ID Auth SDK \(sidecar\) in production environments. It covers essential security controls including network isolation, credential management, token validation, runtime security, and monitoring to ensure your SDK deployment follows security best practices.

Caution

The Microsoft Entra ID Auth SDK \(sidecar\) API must **never** be publicly accessible. It should only be reachable by applications within the same trust boundary \(e.g., same pod, same virtual network\). By default the allowed hosts is localhost. Exposing this API publicly can enable **unauthorized token acquisition**, which is a critical security risk. Also note that all the applications within the same trust boundary will have access to this API. Ensure that every application in that boundary is trusted and properly secured.

## Is it safe to run the SDK?

The Microsoft Entra ID Auth SDK \(sidecar\) is designed with security in mind, but its safety depends on proper configuration and deployment practices. Follow these best practices to ensure a secure deployment:

- Run only in containerized environments
- Restrict access to localhost/pod-internal only
- Use Kubernetes Network Policies
- Store credentials securely \(Key Vault, Secrets\)
- Run as non-root user
- Enable audit logging

## Network security

Network isolation is critical for protecting authentication operations. The Microsoft Entra ID Auth SDK \(sidecar\) must run within trusted boundaries with strict access controls and comprehensive traffic filtering. This includes localhost-only binding, pod-internal communication, and network policies that prevent unauthorized access to authentication endpoints.

### Restrict SDK access

Configure Kestrel to listen only on localhost only to prevent external network access to authentication endpoints:

```yaml
containers:
- name: sidecar
  image: mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0
  env:
  - name: Kestrel__Endpoints__Http__Url
    value: "http://127.0.0.1:5000"
```

Alternatively, use Kestrel's host filtering with AllowedHosts to restrict access:

```yaml
containers:
- name: sidecar
  image: mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0
  env:
  - name: AllowedHosts
    value: "localhost;127.0.0.1"
```

### Use pod-local communication

Configure your application to communicate with the Microsoft Entra ID Auth SDK \(sidecar\) via localhost to ensure traffic remains within the same pod and doesn't traverse the network:

```yaml
containers:
- name: app
  env:
  - name: SIDECAR_URL
    value: "http://localhost:5000" # Pod-local communication only
```

Never expose via LoadBalancer or Ingress \(this would allow unauthorized token acquisition from outside the trusted boundary\):

```yaml
# WRONG - exposes Microsoft Entra ID Auth SDK (sidecar) publicly
apiVersion: v1
kind: Service
metadata:
  name: sidecar-service
spec:
  type: LoadBalancer # Exposes SDK publicly - INSECURE
  selector:
    app: myapp
  ports:
  - port: 5000
```

## Credential management

Secure credential management is fundamental for SDK security. Use managed identities whenever possible to eliminate secrets, and follow the principle of least privilege when configuring authentication credentials.

### Prefer Workload Identity for containers

Use Microsoft Entra Workload ID for containerized deployments \(AKS\) to eliminate secrets entirely and ensure secure credential management with file-based token projection:

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: myapp-sa
  annotations:
    azure.workload.identity/client-id: "<managed-identity-client-id>"

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
spec:
  template:
    metadata:
      labels:
        azure.workload.identity/use: "true"
    spec:
      serviceAccountName: myapp-sa
      containers:
      - name: sidecar
        image: mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0
        env:
        - name: AzureAd__ClientId
          value: "<web-api-client-id>"
        
        # Workload Identity credentials - uses file-based token projection
        - name: AzureAd__ClientCredentials__0__SourceType
          value: "SignedAssertionFilePath"
```

**Benefits**: Workload identity eliminates the need to store or rotate secrets while providing automatic credential management, Azure RBAC integration, and a full audit trail. The token is automatically projected to the pod by the workload identity webhook, and the SDK reads it using the `SignedAssertionFilePath` credential type. This approach significantly reduces security risks and operational overhead compared to traditional secret-based authentication.

**Note**: For Azure VMs and App Services \(non-containerized environments\), use system or user-assigned managed identities with the `SignedAssertionFromManagedIdentity` credential type instead. For more information, see [Use Managed Identity](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/overview).

### Use certificates over secrets

Prefer certificates for authentication when client secrets cannot be avoided. Certificates provide stronger security than client secrets because they use public-key cryptography and are more difficult to extract or misuse. Store certificates in Azure Key Vault for centralized management and automatic renewal:

```yaml
- name: AzureAd__ClientCredentials__0__SourceType
  value: "KeyVault"
- name: AzureAd__ClientCredentials__0__KeyVaultUrl
  value: "https://your-keyvault.vault.azure.net"
- name: AzureAd__ClientCredentials__0__KeyVaultCertificateName
  value: "your-cert-name"
```

**Benefits**: Azure Key Vault provides centralized certificate management with automated rotation, access policies, and comprehensive auditing, while ensuring certificates are never embedded in container images. For more information, see [Use Certificates for Authentication](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/overview).

### Store secrets securely

Kubernetes Secrets is suitable option for storing client secrets if managed identities or certificates are not an option, although ensure secrets are encrypted at rest and access is tightly controlled:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-cert
type: Opaque
data:
  certificate.pfx: <base64-encoded-pfx>
  certificate.password: <base64-encoded-password>

---
containers:
- name: sidecar
  volumeMounts:
  - name: cert-volume
    mountPath: /certs
    readOnly: true
  env:
  - name: AzureAd__ClientCredentials__0__SourceType
    value: "Path"
  - name: AzureAd__ClientCredentials__0__CertificateDiskPath
    value: "/certs/certificate.pfx"
  - name: AzureAd__ClientCredentials__0__CertificatePassword
    valueFrom:
      secretKeyRef:
        name: app-cert
        key: certificate.password

volumes:
- name: cert-volume
  secret:
    secretName: app-cert
    items:
    - key: certificate.pfx
      path: certificate.pfx
    defaultMode: 0400  # Read-only for owner
```

### Client secrets \(avoid if possible\)

If client secrets must be used, implement additional security measures to minimize risk. Client secrets are less secure than managed identities or certificates, so they require extra protection including short expiration periods, secure storage with encryption at rest, restricted access through RBAC, and frequent rotation schedules. Never store secrets in container images or environment variables visible in deployment manifests:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secrets
type: Opaque
stringData:
  client-secret: "<your-client-secret>"

---
containers:
- name: sidecar
  env:
  - name: AzureAd__ClientCredentials__0__SourceType
    value: "ClientSecret"
  - name: AzureAd__ClientCredentials__0__ClientSecret
    valueFrom:
      secretKeyRef:
        name: app-secrets
        key: client-secret
```

Caution

Never commit secrets to source control. Use external secret management \(Azure Key Vault, Sealed Secrets, etc.\).

## Token security

Token security ensures that only valid, appropriately-scoped tokens are accepted and processed by the SDK. Implement token validation, scope requirements, and audience checks to prevent unauthorized access and limit token misuse.

### Enable scope validation

Require specific scopes for incoming tokens \(space separated\):

```yaml
- name: AzureAd__Scopes
  value: "access_as_user"
```

### Set appropriate audience

Configure expected audience for token validation:

```yaml
- name: AzureAd__Audience
  value: "api://your-api-id"
```

Note

The expected audience value depends on your app registration's [**requestedAccessTokenVersion**](https://learn.microsoft.com/en-us/entra/identity-platform/reference-app-manifest#requestedaccesstokenversion-attribute):

- **Version 2**: Use the `{ClientId}` value directly
- **Version 1** or **null**: Use the App ID URI \(typically `api://{ClientId}` unless you customized it\)

### Validate tokens before use

Always call `/Validate` before accepting user tokens:

```bash
GET /Validate
Authorization: Bearer <user-token>
```

### Secure inbound PoP validation

Note

Inbound SHR PoP validation requires sidecar version `1.1.2-preview` or later.

For app-only SHR PoP credentials, derive `original-method` and `original-uri` from the trusted request-processing path. Don't accept replacement values supplied by an untrusted client. The sidecar validates the SHR credential against these values but doesn't observe the original request directly.

The `ts` claim determines SHR expiration using `Sidecar:PopValidation:SignedHttpRequestLifetime`, which defaults to five minutes. This check isn't a replay cache, and server nonce validation isn't supported.

After validation, authorize the app identity using roles, application permissions, or other trusted claims. `AzureAd:Scopes` applies to Bearer validation and isn't used to authorize app-only PoP credentials.

## Runtime security

Runtime security controls protect the SDK container from modification, privilege escalation, and unauthorized capability access. Configure the container to run with minimal privileges and read-only filesystems to reduce the attack surface.

### Read-Only root filesystem

Prevent modification of container filesystem:

```yaml
    securityContext:
      readOnlyRootFilesystem: true
```

The SDK uses in-memory keys and token caches, so no writable mounts are required for read-only deployments.

### Pod security policy

Enforce security standards:

```yaml
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: sidecar-psp
spec:
  privileged: false
  allowPrivilegeEscalation: false
  requiredDropCapabilities:
  - ALL
  runAsUser:
    rule: 'MustRunAsNonRoot'
  seLinux:
    rule: 'MustRunAs'
  fsGroup:
    rule: 'MustRunAs'
  readOnlyRootFilesystem: true
```

## Logging and monitoring

Effective logging and monitoring enable you to detect anomalies, troubleshoot issues, and maintain audit trails for compliance. Configure appropriate logging levels for your environment and implement health probes to ensure the SDK operates as expected.

### Configure appropriate logging

Production environment:

```yaml
- name: Logging__LogLevel__Default
  value: "Warning"
- name: Logging__LogLevel__Microsoft.Identity.Web
  value: "Information"
```

Development environment \(verbose\):

```yaml
- name: Logging__LogLevel__Default
  value: "Debug"
- name: ASPNETCORE_ENVIRONMENT
  value: "Development"
```

### Enable health monitoring

Configure liveness and readiness probes:

```yaml
livenessProbe:
  httpGet:
    path: /health
    port: 5000
  initialDelaySeconds: 10
  periodSeconds: 10
  failureThreshold: 3

readinessProbe:
  httpGet:
    path: /health
    port: 5000
  initialDelaySeconds: 5
  periodSeconds: 5
  failureThreshold: 3
```

## Best practices checklist

Use this comprehensive checklist to ensure your SDK deployment follows all recommended security practices across network, credentials, tokens, runtime, and monitoring dimensions.

Network:

- \[ \] SDK listens only on localhost/127.0.0.1
- \[ \] Never exposed via LoadBalancer or Ingress
- \[ \] Network policies restrict external access
- \[ \] HTTPS/TLS for external communication

Credentials:

- \[ \] Use Workload Identity for containers \(AKS, Kubernetes, Docker\) with `SignedAssertionFilePath`
- \[ \] Use Managed Identity for VMs/App Services with `SignedAssertionFromManagedIdentity`
- \[ \] Prefer certificates over secrets
- \[ \] Secrets stored in secure management system
- \[ \] Regular credential rotation

Tokens:

- \[ \] Scope validation enabled
- \[ \] Audience validation configured
- \[ \] Tokens validated before use

Runtime:

- \[ \] Container runs as non-root
- \[ \] Read-only root filesystem
- \[ \] Security context applied
- \[ \] Resource limits set

Monitoring:

- \[ \] Appropriate logging configured
- \[ \] Health checks enabled
- \[ \] Audit logging enabled
- \[ \] Alerts configured

## Common security patterns

Reference implementations demonstrate how to combine multiple security controls into cohesive deployment patterns. These patterns serve as templates for production deployments in various threat models.

### High-Security deployment

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: secure-app-sa
  annotations:
    azure.workload.identity/client-id: "<managed-identity-id>"

---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: secure-app
spec:
  template:
    metadata:
      labels:
        azure.workload.identity/use: "true"
    spec:
      serviceAccountName: secure-app-sa
      securityContext:
        fsGroup: 1654
      containers:
      - name: sidecar
        image: mcr.microsoft.com/entra-sdk/auth-sidecar:1.0.0
        ports:
        - containerPort: 5000
        env:
        - name: Kestrel__Endpoints__Http__Url
          value: "http://127.0.0.1:5000"
        - name: AzureAd__TenantId
          valueFrom:
            configMapKeyRef:
              name: app-config
              key: tenant-id
        - name: AzureAd__ClientId
          value: "<managed-identity-client-id>"
        securityContext:
          runAsNonRoot: true
          runAsUser: 1654
          runAsGroup: 1654
          readOnlyRootFilesystem: true
          allowPrivilegeEscalation: false
          capabilities:
            drop:
            - ALL
        resources:
          requests:
            memory: "128Mi"
            cpu: "100m"
          limits:
            memory: "256Mi"
            cpu: "250m"
        livenessProbe:
          httpGet:
            path: /health
            port: 5000
          initialDelaySeconds: 10
          periodSeconds: 10
```

### Rotate credentials regularly

Rotating credentials reduces the window of opportunity for attackers if credentials are leaked or compromised. The rotation frequency depends on the credential type and your organization's security policy:

- **Client secrets**: Every 90 days \(recommended\)
- **Certificates**: Before expiration, typically every 1-2 years
- **Keys for Signed HTTP Requests \(SHR\)**: Follow your organization's security policy

**Implementation guidance**: Use Azure Key Vault with automated rotation capabilities or integrate external secret managers \(such as Sealed Secrets\) into your deployment pipeline. This minimizes manual intervention and ensures consistent rotation schedules.

### Respond to compromised credentials

If you suspect that credentials have been compromised, follow these steps immediately to contain the incident and prevent unauthorized access:

1. **Revoke compromised credentials in Microsoft Entra ID** - Remove the credentials from the application registration to block their use immediately.
2. **Generate new credentials** - Create new client secrets or certificates in Microsoft Entra ID to replace the compromised ones.
3. **Update your secrets management system** - Store the new credentials in Kubernetes Secrets or Azure Key Vault with appropriate access controls.
4. **Redeploy SDK containers** - Update your deployments to use the new credentials, ensuring all running instances pick up the changes.
5. **Review access logs** - Check Azure Monitor and Kubernetes audit logs for signs of unauthorized token requests or suspicious activity during the compromise window.
6. **Document the incident** - Record details of the incident \(when discovered, how it happened, what was accessed\) and follow your organization's incident response procedures to prevent recurrence.

## Related content

- [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation)
- [Configuration Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
- [Endpoints Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/endpoints)
- [Troubleshooting](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/troubleshooting)
