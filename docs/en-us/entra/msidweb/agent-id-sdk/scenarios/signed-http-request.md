<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/signed-http-request -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# Scenario: Signed HTTP requests \(SHR\)

Use Signed HTTP Requests \(SHR\) with the Microsoft Entra ID Auth SDK \(sidecar\) to implement proof-of-possession \(PoP\) token security. PoP tokens cryptographically bind tokens to a public key, preventing token theft and replay attacks when calling downstream APIs.

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- **Microsoft Entra ID Auth SDK \(sidecar\)** deployed and running with proof-of-possession support enabled. See [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation) for setup instructions.
- **RSA key pair** - Generate a public/private key pair for cryptographic signing. The public key is configured in the SDK, while the private key remains secure in your application.
- **Downstream API supporting PoP tokens** - The target API must validate proof-of-possession tokens and verify signatures using the public key.
- **Appropriate permissions in Microsoft Entra ID** - Your account must have permissions to register applications and configure PoP settings.

## Generate key pair

Before implementing PoP tokens, generate an RSA key pair. The private key remains in your application for signing requests, while the public key is configured in the Microsoft Entra ID Auth SDK \(sidecar\):

```bash
# Generate RSA private key
openssl genrsa -out private.pem 2048

# Extract public key
openssl rsa -in private.pem -pubout -out public.pem

# Base64 encode public key for configuration
base64 -w 0 public.pem > public.pem.b64

# View base64-encoded key
cat public.pem.b64
```

## Configuration

Configure the Microsoft Entra ID Auth SDK \(sidecar\) with your RSA public key and downstream API settings. Store sensitive keys in secure configuration stores:

### SDK configuration

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: shr-keys
type: Opaque
data:
  public-key: <base64-encoded-public-key>

---
apiVersion: v1
kind: ConfigMap
metadata:
  name: sidecar-config
data:
  # ... other configuration ...
  DownstreamApis__SecureApi__BaseUrl: "https://api.contoso.com"
  DownstreamApis__SecureApi__Scopes: "api://secureapi/.default"
  DownstreamApis__SecureApi__AcquireTokenOptions__PopPublicKey: "<base64-public-key>"
```

## Usage examples

To use PoP tokens in your application, request a PoP token from the Microsoft Entra ID Auth SDK \(sidecar\) by specifying your public key, then include it in API requests:

### TypeScript

```typescript
// Request PoP token
async function getPopToken(incomingToken: string, publicKey: string): Promise<string> {
  const sidecarUrl = process.env.SIDECAR_URL!;
  
  const response = await fetch(
    `${sidecarUrl}/AuthorizationHeader/SecureApi?` +
    `optionsOverride.AcquireTokenOptions.PopPublicKey=${encodeURIComponent(publicKey)}`,
    {
      headers: {
        'Authorization': incomingToken
      }
    }
  );
  
  const data = await response.json();
  return data.authorizationHeader; // Returns "PoP <pop-token>"
}

// Use PoP token with signed request
async function callSecureApi(incomingToken: string, publicKey: string, privateKey: string) {
  // Get PoP token from the SDK
  const popToken = await getPopToken(incomingToken, publicKey);
  
  // Make request to API with PoP token
  const response = await fetch('https://api.contoso.com/secure/data', {
    headers: {
      'Authorization': popToken
    }
  });
  
  return await response.json();
}
```

### Python

```python
import base64
import requests
import os

def get_pop_token(incoming_token: str, public_key: str) -> str:
    """Get a PoP token from the SDK."""
    sidecar_url = os.getenv('SIDECAR_URL', 'http://localhost:5000')
    
    response = requests.get(
        f"{sidecar_url}/AuthorizationHeader/SecureApi",
        params={
            'optionsOverride.AcquireTokenOptions.PopPublicKey': public_key
        },
        headers={'Authorization': incoming_token}
    )
    
    response.raise_for_status()
    data = response.json()
    return data['authorizationHeader']

def call_secure_api(incoming_token: str, public_key_b64: str):
    """Call API with PoP token."""
    pop_token = get_pop_token(incoming_token, public_key_b64)
    
    response = requests.get(
        'https://api.contoso.com/secure/data',
        headers={'Authorization': pop_token}
    )
    
    return response.json()
```

## Per-request SHR

You can override PoP settings on a per-request basis by specifying different public keys for different APIs or scopes:

```typescript
// Enable SHR for specific request
const response = await fetch(
  `${sidecarUrl}/AuthorizationHeader/Graph?` +
  `optionsOverride.AcquireTokenOptions.PopPublicKey=${encodeURIComponent(publicKey)}`,
  {
    headers: { 'Authorization': incomingToken }
  }
);
```

## Key management

Implement secure key management practices to protect your RSA keys and enable key rotation when needed:

### Secure key storage

Store RSA keys securely using Kubernetes Secrets:

```yaml
# Store keys in Kubernetes Secret
apiVersion: v1
kind: Secret
metadata:
  name: shr-keys
type: Opaque
data:
  public-key: <base64-encoded-public-key>
  private-key: <base64-encoded-private-key>

---
# Mount keys in application
volumes:
- name: shr-keys
  secret:
    secretName: shr-keys
    defaultMode: 0400

containers:
- name: app
  volumeMounts:
  - name: shr-keys
    mountPath: /keys
    readOnly: true
```

### Key rotation

Rotate signing keys periodically using OpenSSL and update configurations:

```bash
#!/bin/bash
# Script to rotate SHR keys

# Generate new key pair
openssl genrsa -out private-new.pem 2048
openssl rsa -in private-new.pem -pubout -out public-new.pem
base64 -w 0 public-new.pem > public-new.pem.b64

# Update Kubernetes secret
kubectl create secret generic shr-keys-new \
  --from-file=public-key=public-new.pem.b64 \
  --from-file=private-key=private-new.pem \
  --dry-run=client -o yaml | kubectl apply -f -

# Update deployment to use new keys
kubectl rollout restart deployment myapp
```

## Validating PoP tokens

The downstream API must validate the PoP token to ensure it's correctly signed and bound to the request:

1. Verify JWT signature using the public key extracted from the token
2. Validate standard JWT claims \(issuer, audience, expiration\)
3. Verify the `cnf` claim contains the expected public key
4. Validate that the HTTP request signature matches using the key from the `cnf` claim

To validate inbound app-only SHR PoP credentials with the Microsoft Entra ID Auth SDK \(sidecar\), see [Validate an authorization header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/validate-authorization-header).

## Benefits

Implementing Signed HTTP Requests with proof-of-possession tokens provides several security advantages:

- **Token Binding**: Each token is cryptographically bound to a specific public key, preventing unauthorized use even if intercepted.
- **Replay Prevention**: An attacker cannot replay a captured token without possessing the corresponding private key.
- **Enhanced Security**: Provides protection against token theft, especially important for sensitive operations and high-security environments.
- **Proof of Possession**: Cryptographically proves that the client holds the private key corresponding to the token.

## Best practices

When implementing Signed HTTP Requests, follow these practices to maintain security and operational reliability:

- **Secure Private Keys**: Never expose private keys in logs, configuration files, or code repositories. Store them securely using key vaults or configuration management systems.
- **Rotate Keys Regularly**: Implement a key rotation schedule to minimize the impact of potential key compromise. Update both the SDK and downstream APIs during rotation.
- **Use Per-API Keys**: Use different key pairs for different APIs or security zones to limit the impact if one key is compromised.
- **Monitor Usage**: Audit and monitor PoP token usage to detect suspicious patterns or unauthorized access attempts.
- **Test Thoroughly**: Verify that PoP token validation works correctly before deploying to production, ensuring both signature validation and request binding checks pass.

## Related content

- [Validate an authorization header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/validate-authorization-header)
- [Security](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)
- [Obtain an authorization header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/obtain-authorization-header)
- [Configuration](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
- [Troubleshooting](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/troubleshooting)
