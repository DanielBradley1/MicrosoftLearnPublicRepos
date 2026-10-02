<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/validate-authorization-header -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Scenario: Validate an authorization header

Validate incoming Bearer or app-only Signed HTTP Request \(SHR\) Proof-of-Possession tokens by forwarding them to the Microsoft Entra ID Auth SDK \(sidecar\)'s `/Validate` endpoint, then extract the returned claims to make authorization decisions. This guide shows you how to implement token validation middleware and make authorization decisions based on scopes or roles.

Note

Inbound SHR PoP validation is supported in sidecar version `1.1.2-preview` and later.

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- **Microsoft Entra ID Auth SDK \(sidecar\)** version `1.1.2-preview` or later deployed and running with network access from your application. See the [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation) for setup instructions and use the appropriate supported image variant.
- **Registered application in Microsoft Entra ID** - Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com), configured for *Accounts in this organizational directory only*. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp) for more details. Record the following values from the application **Overview** page:

  - Application \(client\) ID
  - Directory \(tenant\) ID
  - Configure an **App ID URI** in the **Expose an API** section \(used as the audience for token validation\)

- **Bearer tokens from authenticated clients** - Your application must receive tokens from client applications through OAuth 2.0 flows.
- **App-only access token for PoP validation** - The PoP path doesn't accept delegated or user access tokens.
- **Appropriate permissions in Microsoft Entra ID** - Your account must have permissions to register applications and configure authentication settings.

## Configuration

To validate tokens for your API, configure the Microsoft Entra ID Auth SDK \(sidecar\) with your Microsoft Entra ID tenant information.

```yaml
env:
- name: AzureAd__Instance
  value: "https://login.microsoftonline.com/"
- name: AzureAd__TenantId
  value: "your-tenant-id"
- name: AzureAd__ClientId
  value: "your-api-client-id"
- name: AzureAd__Audience
  value: "api://your-api-id"
```

These `AzureAd` settings validate Bearer tokens and the access token embedded in an SHR credential. `AzureAd__Scopes` applies to Bearer validation, but not to app-only PoP tokens.

### PoP validation settings

PoP support is registered automatically, there is no separate enable switch. Configure `Sidecar__PopValidation` only when you need to change the secure request-binding defaults.

| Configuration key | Default | Description |
| --- | --- | --- |
| `Sidecar__PopValidation__ValidateM` | `true` | Validate the `m` claim against the original HTTP method. |
| `Sidecar__PopValidation__ValidateU` | `true` | Validate that the `u` claim matches either the original URI host or its host and port. |
| `Sidecar__PopValidation__ValidateP` | `true` | Validate the `p` claim against the path in the original URI. |
| `Sidecar__PopValidation__ValidateQ` | `false` | Validate signed query parameters in the `q` claim. |
| `Sidecar__PopValidation__AcceptUnsignedQueryParameters` | `true` | Allow query parameters that aren't covered by the SHR signature. |
| `Sidecar__PopValidation__ValidatePresentClaims` | `false` | Validate the claims listed in `ClaimsToValidateWhenPresent` whenever those claims are present. |
| `Sidecar__PopValidation__SignedHttpRequestLifetime` | `00:05:00` | Set how long the SHR remains valid after the time in its `ts` claim. The value must be greater than zero or sidecar startup fails. The embedded access token lifetime is validated separately. |
| `Sidecar__PopValidation__ClaimsToValidateWhenPresent__<index>` | `m`, `p` | Define the indexed list used when `ValidatePresentClaims` is `true`. Don't include `h` or `b`; the sidecar doesn't receive the original request headers or body. |

`ValidateTs`, `ValidateH`, `ValidateB`, and `AcceptUnsignedHeaders` aren't individually configurable sidecar options. Timestamp \(`ts`\) validation is always enabled. The sidecar sets header \(`h`\) and body-hash \(`b`\) validation off and accepts unsigned headers because it receives only the original request line. However, `ValidatePresentClaims` can invoke validation for a listed claim when that claim is present. Don't add `h` or `b` to `ClaimsToValidateWhenPresent`, because the information required to validate them isn't available. The sidecar doesn't enforce a server nonce or replay cache protection, and it doesn't resolve PoP signing keys from remote `jku` URLs.

## Supported validation schemes

The `/Validate` endpoint accepts both Bearer and PoP credentials:

| Scheme | Supported token | Request information |
| --- | --- | --- |
| `Bearer` | Access token presented directly using the Bearer scheme | `Authorization` header |
| `PoP` | App-only access token embedded in an SHR credential | `Authorization`, `original-method`, and absolute `original-uri` headers |

Bearer request:

```http
GET /Validate HTTP/1.1
Authorization: Bearer <access-token>
```

PoP request:

```http
GET /Validate HTTP/1.1
Authorization: PoP <signed-http-request>
original-method: GET
original-uri: https://api.contoso.com/data
```

For PoP, `original-method` and `original-uri` must represent the request line that the SHR credential was signed over. By default, the sidecar validates the method, host with or without its port, path, and timestamp. It validates query parameters only when `ValidateQ` is enabled. Behind a reverse proxy or TLS terminator, configure your framework to process forwarded headers only from trusted proxies, or construct the URI from trusted canonical routing metadata. Don't forward client-supplied `original-method` or `original-uri` values unchanged. The call to `/Validate` isn't itself the signed resource request.

A successful response sets `protocol` to `Bearer` or `PoP`. For PoP, `token` contains the validated access token embedded in the SHR credential. A failed PoP request returns `401 Unauthorized` with `WWW-Authenticate: PoP error="invalid_token"`. The response can also contain the Bearer challenge because `/Validate` accepts both schemes.

Important

Inbound PoP validation supports app-only access tokens. It doesn't support delegated or user tokens, OBO or actor-token flows, mTLS PoP, or PFT/CDT-over-PoP.

For complete adapter examples, see the [TypeScript adapter](https://github.com/AzureAD/microsoft-identity-web/blob/master/tests/DevApps/SidecarAdapter/typescript/README.md) and [Python adapter](https://github.com/AzureAD/microsoft-identity-web/blob/master/tests/DevApps/SidecarAdapter/python/README.md).

Before adapting these development examples for production, replace any request-derived scheme or host with a canonical external origin from trusted configuration, and preserve the encoded request target at the trusted server or proxy boundary.

For a PoP configuration example, see the [sidecar appsettings configuration](https://github.com/AzureAD/microsoft-identity-web/blob/master/src/Microsoft.Identity.Web.Sidecar/appsettings.json#L42-L53).

## TypeScript/Node.js

The following implementation shows how to create token validation middleware that integrates with the Microsoft Entra ID Auth SDK \(sidecar\) using TypeScript or JavaScript. Bearer requests forward the `Authorization` header. PoP requests also forward the original method and absolute URI:

This example uses the built-in Fetch API in Node.js 18 or later.

```typescript
interface ValidateResponse {
  protocol: string;
  token: string;
  claims: {
    aud: string;
    iss: string;
    oid?: string;
    sub?: string;
    tid?: string;
    upn?: string;
    scp?: string;
    roles?: string[];
    [key: string]: unknown;
  };
}

class TokenValidationError extends Error {
  constructor(
    public readonly status: number,
    public readonly challenges: string[]
  ) {
    super(`Token validation failed with status ${status}`);
  }
}

async function validateToken(
  authorizationHeader: string,
  originalMethod?: string,
  originalUri?: string
): Promise<ValidateResponse> {
  const sidecarUrl = process.env.SIDECAR_URL || 'http://localhost:5000';

  const headers: Record<string, string> = {
    'Authorization': authorizationHeader
  };

  if (authorizationHeader.toLowerCase().startsWith('pop ')) {
    if (!originalMethod || !originalUri) {
      throw new Error(
        'PoP validation requires the original HTTP method and absolute URI.'
      );
    }

    headers['original-method'] = originalMethod;
    headers['original-uri'] = originalUri;
  }

  const response = await fetch(`${sidecarUrl}/Validate`, {
    headers
  });
  
  if (!response.ok) {
    const challenge = response.headers.get('www-authenticate');
    throw new TokenValidationError(
      response.status,
      challenge ? [challenge] : []
    );
  }
  
  return await response.json() as ValidateResponse;
}
```

The following snippet demonstrates how to use the `validateToken` function in an Express.js middleware to protect API endpoints. Set `EXTERNAL_ORIGIN` to the trusted external scheme and host. The trusted server or proxy boundary must preserve the encoded original request target in `req.originalUrl`, including any path prefix and query string.

```javascript
// Express.js middleware example
import express from 'express';

const app = express();
const externalOrigin = process.env.EXTERNAL_ORIGIN?.replace(/\/+$/, '');

if (!externalOrigin) {
  throw new Error(
    'EXTERNAL_ORIGIN must contain the trusted external scheme and host.'
  );
}

// Token validation middleware
async function requireAuth(req, res, next) {
  const authHeader = req.headers.authorization;
  
  if (!authHeader) {
    return res.status(401).json({ error: 'No authorization token provided' });
  }
  
  try {
    let validation;
    if (authHeader.toLowerCase().startsWith('pop ')) {
      const originalUri = `${externalOrigin}${req.originalUrl}`;
      validation = await validateToken(
        authHeader,
        req.method,
        originalUri
      );
    } else {
      validation = await validateToken(authHeader);
    }
    
    // Attach claims to request object
    req.user = {
      id: validation.claims.oid,
      upn: validation.claims.upn,
      tenantId: validation.claims.tid,
      scopes: validation.claims.scp?.split(' ') || [],
      roles: validation.claims.roles || [],
      claims: validation.claims
    };
    
    next();
  } catch (error) {
    console.error('Token validation failed:', error);
    if (error instanceof TokenValidationError) {
      for (const challenge of error.challenges) {
        res.append('WWW-Authenticate', challenge);
      }
      return res.status(error.status).json({ error: 'Invalid token' });
    }

    return res.status(502).json({ error: 'Token validation unavailable' });
  }
}

// Protected endpoint
app.get('/api/protected', requireAuth, (req, res) => {
  res.json({
    message: 'Access granted',
    user: {
      id: req.user.id,
      upn: req.user.upn
    }
  });
});

// Scope-based authorization
app.get('/api/admin', requireAuth, (req, res) => {
  if (!req.user.roles.includes('Admin')) {
    return res.status(403).json({ error: 'Insufficient permissions' });
  }
  
  res.json({ message: 'Admin access granted' });
});

app.listen(8080);
```

## Python

The following Python snippet uses Flask decorators to wrap route handlers with token validation. Bearer requests forward the `Authorization` header. PoP requests also forward the original method and absolute URI:

For PoP requests, configure the WSGI server or trusted proxy to preserve the original encoded request target, including the query string, in `RAW_URI` or `REQUEST_URI`. Support for these environment values is server-specific. Set `EXTERNAL_ORIGIN` to the trusted external scheme and host, and don't derive it from client-supplied headers. If a proxy rewrites the path or query string, it must preserve the pre-rewrite raw target at the application boundary.

```python
import os
import requests
from flask import Flask, request, jsonify
from functools import wraps

app = Flask(__name__)
app.config['EXTERNAL_ORIGIN'] = os.environ['EXTERNAL_ORIGIN'].rstrip('/')

class TokenValidationError(Exception):
    def __init__(self, status_code: int, challenges: list[str]):
        super().__init__(f'Token validation failed with status {status_code}')
        self.status_code = status_code
        self.challenges = challenges

def get_original_uri() -> str:
    raw_target = (
        request.environ.get('RAW_URI')
        or request.environ.get('REQUEST_URI')
    )
    if not raw_target or not raw_target.startswith('/'):
        raise RuntimeError(
            'PoP validation requires a WSGI server or trusted proxy that '
            'preserves the origin-form raw request target.'
        )

    return f"{app.config['EXTERNAL_ORIGIN']}{raw_target}"

def validate_token(
    authorization_header: str,
    original_method: str = '',
    original_uri: str = ''
) -> dict:
    """Validate token using the SDK."""
    sidecar_url = os.getenv('SIDECAR_URL', 'http://localhost:5000')

    headers = {'Authorization': authorization_header}
    if authorization_header.lower().startswith('pop '):
        if not original_method or not original_uri:
            raise ValueError(
                'PoP validation requires the original HTTP method and absolute URI.'
            )
        headers['original-method'] = original_method
        headers['original-uri'] = original_uri

    response = requests.get(
        f"{sidecar_url}/Validate",
        headers=headers
    )
    
    if not response.ok:
        raise TokenValidationError(
            response.status_code,
            response.raw.headers.getlist('WWW-Authenticate')
        )
    
    return response.json()

# Token validation decorator
def require_auth(f):
    @wraps(f)
    def decorated_function(*args, **kwargs):
        auth_header = request.headers.get('Authorization')
        
        if not auth_header:
            return jsonify({'error': 'No authorization token provided'}), 401
        
        try:
            if auth_header.lower().startswith('pop '):
                validation = validate_token(
                    auth_header,
                    request.method,
                    get_original_uri()
                )
            else:
                validation = validate_token(auth_header)
            
            # Attach user info to Flask's g object
            from flask import g
            g.user = {
                'id': validation['claims']['oid'],
                'upn': validation['claims'].get('upn'),
                'tenant_id': validation['claims']['tid'],
                'scopes': validation['claims'].get('scp', '').split(' '),
                'roles': validation['claims'].get('roles', []),
                'claims': validation['claims']
            }
            
            return f(*args, **kwargs)
        except TokenValidationError as error:
            response = jsonify({'error': 'Invalid token'})
            response.status_code = error.status_code
            for challenge in error.challenges:
                response.headers.add('WWW-Authenticate', challenge)
            return response
        except Exception as error:
            print(f"Token validation failed: {error}")
            return jsonify({'error': 'Token validation unavailable'}), 502
    
    return decorated_function

# Protected endpoint
@app.route('/api/protected')
@require_auth
def protected():
    from flask import g
    return jsonify({
        'message': 'Access granted',
        'user': {
            'id': g.user['id'],
            'upn': g.user['upn']
        }
    })

# Role-based authorization
@app.route('/api/admin')
@require_auth
def admin():
    from flask import g
    if 'Admin' not in g.user['roles']:
        return jsonify({'error': 'Insufficient permissions'}), 403
    
    return jsonify({'message': 'Admin access granted'})

if __name__ == '__main__':
    app.run(port=8080)
```

## Go

The following Go implementation demonstrates token validation using the standard HTTP handler pattern. Bearer requests forward the `Authorization` header. PoP requests also forward the original method and absolute URI. Set `EXTERNAL_ORIGIN` to the trusted external scheme and host. The trusted server or proxy boundary must preserve the encoded original request target in `RequestURI`, including any path prefix and query string:

```go
package main

import (
    "encoding/json"
    "errors"
    "fmt"
    "net/http"
    "os"
    "strings"
)

type ValidateResponse struct {
    Protocol string                 `json:"protocol"`
    Token    string                 `json:"token"`
    Claims   map[string]interface{} `json:"claims"`
}

type User struct {
    ID       string
    UPN      string
    TenantID string
    Scopes   []string
    Roles    []string
    Claims   map[string]interface{}
}

type OriginalRequest struct {
    Method string
    URI    string
}

type TokenValidationError struct {
    StatusCode int
    Challenges []string
}

func (e *TokenValidationError) Error() string {
    return fmt.Sprintf("token validation failed with status %d", e.StatusCode)
}

func hasPoPScheme(authHeader string) bool {
    return len(authHeader) >= 4 && strings.EqualFold(authHeader[:4], "PoP ")
}

func getOriginalURI(r *http.Request) (string, error) {
    externalOrigin := strings.TrimRight(os.Getenv("EXTERNAL_ORIGIN"), "/")
    if externalOrigin == "" {
        return "", fmt.Errorf(
            "EXTERNAL_ORIGIN must contain the trusted external scheme and host",
        )
    }
    if r.RequestURI == "" || !strings.HasPrefix(r.RequestURI, "/") {
        return "", fmt.Errorf(
            "the trusted server or proxy must preserve the origin-form raw request target",
        )
    }

    return externalOrigin + r.RequestURI, nil
}

func validateToken(
    authHeader string,
    originalRequest *OriginalRequest,
) (*ValidateResponse, error) {
    sidecarURL := os.Getenv("SIDECAR_URL")
    if sidecarURL == "" {
        sidecarURL = "http://localhost:5000"
    }
    
    req, err := http.NewRequest("GET", fmt.Sprintf("%s/Validate", sidecarURL), nil)
    if err != nil {
        return nil, err
    }
    
    req.Header.Set("Authorization", authHeader)

    if hasPoPScheme(authHeader) {
        if originalRequest == nil ||
            originalRequest.Method == "" ||
            originalRequest.URI == "" {
            return nil, fmt.Errorf(
                "PoP validation requires the original HTTP method and absolute URI",
            )
        }
        req.Header.Set("original-method", originalRequest.Method)
        req.Header.Set("original-uri", originalRequest.URI)
    }
    
    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        return nil, err
    }
    defer resp.Body.Close()
    
    if resp.StatusCode != http.StatusOK {
        return nil, &TokenValidationError{
            StatusCode: resp.StatusCode,
            Challenges: resp.Header.Values("WWW-Authenticate"),
        }
    }
    
    var validation ValidateResponse
    if err := json.NewDecoder(resp.Body).Decode(&validation); err != nil {
        return nil, err
    }
    
    return &validation, nil
}

// Middleware for token validation
func requireAuth(next http.HandlerFunc) http.HandlerFunc {
    return func(w http.ResponseWriter, r *http.Request) {
        authHeader := r.Header.Get("Authorization")
        
        if authHeader == "" {
            http.Error(w, "No authorization token provided", http.StatusUnauthorized)
            return
        }
        
        var originalRequest *OriginalRequest
        if hasPoPScheme(authHeader) {
            originalURI, err := getOriginalURI(r)
            if err != nil {
                http.Error(w, err.Error(), http.StatusInternalServerError)
                return
            }
            originalRequest = &OriginalRequest{
                Method: r.Method,
                URI:    originalURI,
            }
        }

        validation, err := validateToken(authHeader, originalRequest)
        if err != nil {
            var validationError *TokenValidationError
            if errors.As(err, &validationError) {
                for _, challenge := range validationError.Challenges {
                    w.Header().Add("WWW-Authenticate", challenge)
                }
                http.Error(w, "Invalid token", validationError.StatusCode)
            } else {
                http.Error(w, "Token validation unavailable", http.StatusBadGateway)
            }
            return
        }
        
        // Extract user information from claims
        user := &User{
            Claims: validation.Claims,
        }

        if oid, ok := validation.Claims["oid"].(string); ok {
            user.ID = oid
        }

        if tid, ok := validation.Claims["tid"].(string); ok {
            user.TenantID = tid
        }
        
        if upn, ok := validation.Claims["upn"].(string); ok {
            user.UPN = upn
        }
        
        if scp, ok := validation.Claims["scp"].(string); ok {
            user.Scopes = strings.Split(scp, " ")
        }
        
        if roles, ok := validation.Claims["roles"].([]interface{}); ok {
            for _, role := range roles {
                if roleName, ok := role.(string); ok {
                    user.Roles = append(user.Roles, roleName)
                }
            }
        }
        
        // Store user in context (simplified - use context.Context in production)
        r.Header.Set("X-User-ID", user.ID)
        r.Header.Set("X-User-UPN", user.UPN)
        
        next(w, r)
    }
}

func protectedHandler(w http.ResponseWriter, r *http.Request) {
    w.Header().Set("Content-Type", "application/json")
    json.NewEncoder(w).Encode(map[string]interface{}{
        "message": "Access granted",
        "user": map[string]string{
            "id":  r.Header.Get("X-User-ID"),
            "upn": r.Header.Get("X-User-UPN"),
        },
    })
}

func main() {
    http.HandleFunc("/api/protected", requireAuth(protectedHandler))
    
    fmt.Println("Server starting on :8080")
    http.ListenAndServe(":8080", nil)
}
```

## C#

Set `EXTERNAL_ORIGIN` to the trusted external scheme and host. Ensure the trusted server or proxy boundary preserves the encoded path and query exposed through `GetEncodedPathAndQuery()`.

The following C# implementation demonstrates token validation using ASP.NET Core middleware. Bearer requests forward the `Authorization` header. PoP requests also forward the original method and absolute URI:

```csharp
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.Http.Extensions;
using System.Linq;
using System.Net.Http;
using System.Net.Http.Json;
using System.Text.Json;

public class ValidateResponse
{
    public string Protocol { get; set; } = string.Empty;
    public string Token { get; set; } = string.Empty;
    public JsonElement Claims { get; set; }
}

public sealed class TokenValidationException : Exception
{
    public int StatusCode { get; }
    public string[] Challenges { get; }

    public TokenValidationException(int statusCode, string[] challenges)
        : base($"Token validation failed with status {statusCode}")
    {
        StatusCode = statusCode;
        Challenges = challenges;
    }
}

public class TokenValidationService
{
    private readonly HttpClient _httpClient;
    private readonly string _sidecarUrl;
    
    public TokenValidationService(IHttpClientFactory httpClientFactory, IConfiguration config)
    {
        _httpClient = httpClientFactory.CreateClient();
        _sidecarUrl = config["SIDECAR_URL"] ?? "http://localhost:5000";
    }
    
    public async Task<ValidateResponse> ValidateTokenAsync(
        string authorizationHeader,
        string? originalMethod = null,
        string? originalUri = null)
    {
        var request = new HttpRequestMessage(HttpMethod.Get, $"{_sidecarUrl}/Validate");
        request.Headers.Add("Authorization", authorizationHeader);

        if (authorizationHeader.StartsWith("PoP ", StringComparison.OrdinalIgnoreCase))
        {
            if (string.IsNullOrEmpty(originalMethod) || string.IsNullOrEmpty(originalUri))
            {
                throw new ArgumentException(
                    "PoP validation requires the original HTTP method and absolute URI.");
            }

            request.Headers.Add("original-method", originalMethod);
            request.Headers.Add("original-uri", originalUri);
        }

        var response = await _httpClient.SendAsync(request);

        if (!response.IsSuccessStatusCode)
        {
            var challenges = response.Headers.WwwAuthenticate
                .Select(challenge => challenge.ToString())
                .ToArray();
            throw new TokenValidationException((int)response.StatusCode, challenges);
        }
        
        return await response.Content.ReadFromJsonAsync<ValidateResponse>()
            ?? throw new HttpRequestException(
                "The sidecar returned an empty validation response.");
    }
}

// Middleware example
public class TokenValidationMiddleware
{
    private readonly RequestDelegate _next;
    private readonly TokenValidationService _validationService;
    private readonly string _externalOrigin;
    
    public TokenValidationMiddleware(
        RequestDelegate next,
        TokenValidationService validationService,
        IConfiguration config)
    {
        _next = next;
        _validationService = validationService;
        _externalOrigin = (config["EXTERNAL_ORIGIN"]
            ?? throw new InvalidOperationException(
                "EXTERNAL_ORIGIN must contain the trusted external scheme and host."))
            .TrimEnd('/');
    }
    
    public async Task InvokeAsync(HttpContext context)
    {
        var authHeader = context.Request.Headers["Authorization"].ToString();
        
        if (string.IsNullOrEmpty(authHeader))
        {
            context.Response.StatusCode = 401;
            await context.Response.WriteAsJsonAsync(new { error = "No authorization token" });
            return;
        }
        
        try
        {
            ValidateResponse validation;
            if (authHeader.StartsWith("PoP ", StringComparison.OrdinalIgnoreCase))
            {
                var originalUri =
                    $"{_externalOrigin}{context.Request.GetEncodedPathAndQuery()}";
                validation = await _validationService.ValidateTokenAsync(
                    authHeader,
                    context.Request.Method,
                    originalUri);
            }
            else
            {
                validation = await _validationService.ValidateTokenAsync(authHeader);
            }
            
            // Store claims in HttpContext.Items for use in controllers
            context.Items["UserClaims"] = validation.Claims;
            if (validation.Claims.TryGetProperty("oid", out JsonElement oid) &&
                oid.ValueKind == JsonValueKind.String)
            {
                context.Items["UserId"] = oid.GetString();
            }
            
            await _next(context);
        }
        catch (TokenValidationException ex)
        {
            foreach (var challenge in ex.Challenges)
            {
                context.Response.Headers.Append("WWW-Authenticate", challenge);
            }
            context.Response.StatusCode = ex.StatusCode;
            await context.Response.WriteAsJsonAsync(new { error = "Invalid token" });
        }
        catch (Exception ex) when (
            ex is HttpRequestException or JsonException or NotSupportedException)
        {
            context.Response.StatusCode = 502;
            await context.Response.WriteAsJsonAsync(
                new { error = "Token validation unavailable" });
        }
    }
}

// Controller example
[ApiController]
[Route("api")]
public class ProtectedController : ControllerBase
{
    [HttpGet("protected")]
    public IActionResult GetProtected()
    {
        var userId = HttpContext.Items["UserId"] as string;
        
        return Ok(new
        {
            message = "Access granted",
            user = new { id = userId }
        });
    }
}
```

## Extracting specific claims

After validating a token, you can extract the claims to make authorization decisions in your application. The `/Validate` endpoint returns a claims object with the following information:

```json
{
  "protocol": "Bearer",
  "claims": {
    "oid": "user-object-id",
    "upn": "user@contoso.com",
    "tid": "tenant-id",
    "scp": "User.Read Mail.Read",
    "roles": ["Admin"]
  }
}
```

**Common claims include:**

- **`oid`**: Object ID of the user or client service principal represented by the token
- **`upn`**: User principal name for a delegated user token; this claim is typically absent from app-only tokens
- **`tid`**: ID of the tenant that issued the token
- **`scp`**: Delegated scopes the user granted to your application
- **`roles`**: Application roles granted to the represented identity; for app-only tokens, these values represent application permissions or app roles granted to the client

For a PoP response, `protocol` is `PoP`, and the claims describe an application identity rather than a delegated user. Use application roles or other trusted app claims for authorization; don't require delegated scopes.

The following examples show how to extract specific claims from the validation response:

**User Identity**:

```typescript
// Extract user identity
const userId = validation.claims.oid;  // Object ID
const userPrincipalName = validation.claims.upn;  // User Principal Name
const tenantId = validation.claims.tid;  // Tenant ID
```

**Scopes and Roles**:

```typescript
// Extract scopes (delegated permissions)
const scopes = validation.claims.scp?.split(' ') || [];

// Check for specific scope
if (scopes.includes('User.Read')) {
  // Allow access
}

// Extract roles (application permissions)
const roles = validation.claims.roles || [];

// Check for specific role
if (roles.includes('Admin')) {
  // Allow admin access
}
```

## Authorization patterns

After validating tokens, enforce authorization based on the token's claims rather than the authentication scheme. Use delegated scopes when the validated token contains `scp` or `scope` claims. Use application roles or other trusted app claims for app-only tokens, whether they're presented directly or embedded in a PoP credential. Inbound PoP validation supports only app-only tokens.

### Scope-based authorization

Check if a delegated token includes required scopes before granting access:

```typescript
function requireScopes(requiredScopes: string[]) {
  return async (req, res, next) => {
    const validation = await validateToken(req.headers.authorization);
    const userScopes = validation.claims.scp?.split(' ') || [];
    const hasAllScopes = requiredScopes.every(s => userScopes.includes(s));
    
    if (!hasAllScopes) {
      return res.status(403).json({ error: 'Insufficient scopes' });
    }
    next();
  };
}

app.get('/api/mail', requireScopes(['Mail.Read']), (req, res) => {
  res.json({ message: 'Mail access granted' });
});
```

### Role-based authorization

Check if an app-only identity has required application roles:

```typescript
function requireRoles(requiredRoles: string[]) {
  return (req, res, next) => {
    const identityRoles = req.user?.roles || [];
    const hasRole = requiredRoles.some(r => identityRoles.includes(r));
    
    if (!hasRole) {
      return res.status(403).json({ error: 'Insufficient permissions' });
    }
    next();
  };
}

app.delete('/api/resource', requireAuth, requireRoles(['Admin']), (req, res) => {
  res.json({ message: 'Resource deleted' });
});
```

## Error handling

Token validation can fail because the credential is expired or invalid, or because a directly presented access token doesn't satisfy the scopes configured in `AzureAd:Scopes`. Missing application roles or other trusted app claims are application-layer authorization failures after `/Validate` succeeds. Implement error handling that distinguishes between these scenarios. For a PoP credential, pass the original method and URI to this helper:

```typescript
async function validateTokenSafely(
  authHeader: string,
  originalMethod?: string,
  originalUri?: string
): Promise<ValidateResponse | null> {
  try {
    return await validateToken(authHeader, originalMethod, originalUri);
  } catch (error: unknown) {
    if (error instanceof TokenValidationError && error.status === 401) {
      console.error('Token is invalid or expired');
    } else if (error instanceof TokenValidationError && error.status === 403) {
      console.error('Token lacks a required configured scope');
    } else if (error instanceof Error) {
      console.error('Token validation error:', error.message);
    } else {
      console.error('Unknown token validation error');
    }
    return null;
  }
}
```

### Common validation errors

| Error | Cause | Solution |
| --- | --- | --- |
| 401 Unauthorized with a Bearer challenge | Missing or malformed Authorization header | Send a valid Bearer or PoP credential |
| 401 Unauthorized with a Bearer challenge | Invalid or expired Bearer token | Request a new token from the client |
| 401 Unauthorized with a `PoP` challenge | Invalid SHR signature, expired `ts`, request-binding mismatch, or unsupported embedded token type | Verify the SHR and app-only access token, and confirm the original method and URI |
| 401 Unauthorized for a PoP request | Missing `original-method` or `original-uri` | Forward both headers from the original signed request |
| 403 Forbidden from `/Validate` | Directly presented access token doesn't satisfy the scopes configured in `AzureAd:Scopes` | Request a delegated token with a required scope or update the configured scope requirement |
| 403 Forbidden from the application | Validated app identity lacks a required application role or other trusted claim | Assign the required role or update the application's authorization policy |

## Response structure

The `/Validate` endpoint returns:

```json
{
  "protocol": "Bearer",
  "token": "******",
  "claims": {
    "aud": "api://your-api-id",
    "iss": "https://sts.windows.net/tenant-id/",
    "iat": 1234567890,
    "nbf": 1234567890,
    "exp": 1234571490,
    "oid": "user-object-id",
    "sub": "subject",
    "tid": "tenant-id",
    "upn": "user@contoso.com",
    "scp": "User.Read Mail.Read",
    "roles": ["Admin"]
  }
}
```

The `protocol` property is `Bearer` or `PoP`, depending on the authentication scheme that `/Validate` successfully processed. For PoP, `token` contains the validated access token embedded in the SHR credential, and `claims` contains only the claims from that embedded access token. Claims from the outer SHR, such as `resourceProvider`, aren't returned.

## Best practices

1. **Validate Early**: Validate tokens at the API gateway or entry point
2. **Authorize the Identity**: Verify delegated scopes for delegated tokens and application roles, application permissions, or other trusted claims for app-only tokens, including those embedded in PoP credentials
3. **Log Failures**: Log validation failures for security monitoring
4. **Handle Errors**: Provide clear error messages for debugging
5. **Use Middleware**: Implement validation as middleware for consistency
6. **Secure SDK**: Ensure the SDK is only accessible from your application

## Related content

- [Obtain an authorization header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/obtain-authorization-header)
- [Call a downstream API](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/call-downstream-api)
- [Security](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)
- [Using from TypeScript](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-typescript)
