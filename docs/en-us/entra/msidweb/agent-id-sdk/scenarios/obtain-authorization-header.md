<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/obtain-authorization-header -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Scenario: Obtain an authorization header

Exchange incoming bearer tokens for authorization headers scoped to downstream APIs using the Microsoft Entra ID Auth SDK \(sidecar\)'s `/AuthorizationHeader` endpoint. This approach gives you full control over HTTP requests while delegating token acquisition to the SDK.

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- **Microsoft Entra ID Auth SDK \(sidecar\)** deployed and running in your environment. See [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation) for setup instructions.
- **Downstream API configured** in the SDK with the base URL and required scopes for token exchange.
- **Bearer tokens from authenticated clients** - Your application receives tokens from client applications that you'll exchange for downstream API tokens.
- **Appropriate permissions in Microsoft Entra ID** - Your account must have permissions to register applications and grant API permissions.

## Configuration

Configure the downstream API in your Microsoft Entra ID Auth SDK \(sidecar\) with the base URL, required scopes, and optional relative path:

```yaml
env:
- name: DownstreamApis__Graph__BaseUrl
  value: "https://graph.microsoft.com/v1.0"
- name: DownstreamApis__Graph__Scopes
  value: "User.Read Mail.Read"
```

## TypeScript/Node.js

Create a TypeScript function to call the Microsoft Entra ID Auth SDK \(sidecar\) and obtain an authorization header. You can then use this header with your HTTP client to call downstream APIs:

```typescript
import fetch from 'node-fetch';

interface AuthHeaderResponse {
  authorizationHeader: string;
}

async function getAuthorizationHeader(
  incomingToken: string,
  serviceName: string
): Promise<string> {
  const sidecarUrl = process.env.SIDECAR_URL || 'http://localhost:5000';
  
  const response = await fetch(
    `${sidecarUrl}/AuthorizationHeader/${serviceName}`,
    {
      headers: {
        'Authorization': incomingToken
      }
    }
  );
  
  if (!response.ok) {
    throw new Error(`Failed to get authorization header: ${response.statusText}`);
  }
  
  const data = await response.json() as AuthHeaderResponse;
  return data.authorizationHeader;
}

// Usage example
async function getUserProfile(incomingToken: string) {
  // Get authorization header for Microsoft Graph
  const authHeader = await getAuthorizationHeader(incomingToken, 'Graph');
  
  // Use the authorization header to call Microsoft Graph
  const graphResponse = await fetch(
    'https://graph.microsoft.com/v1.0/me',
    {
      headers: {
        'Authorization': authHeader
      }
    }
  );
  
  return await graphResponse.json();
}
```

The following example demonstrates how to integrate this function into an Express.js application using middleware and route handlers:

```javascript
// Express.js middleware example
import express from 'express';

const app = express();

app.get('/api/profile', async (req, res) => {
  try {
    const incomingToken = req.headers.authorization;
    if (!incomingToken) {
      return res.status(401).json({ error: 'No authorization token provided' });
    }
    
    const profile = await getUserProfile(incomingToken);
    res.json(profile);
  } catch (error) {
    console.error('Error fetching profile:', error);
    res.status(500).json({ error: 'Failed to fetch profile' });
  }
});
```

## Python

The following snippet demonstrates a Python function that calls the Microsoft Entra ID Auth SDK \(sidecar\) and obtains an authorization header.

```python
import os
import requests
from typing import Dict, Any

def get_authorization_header(incoming_token: str, service_name: str) -> str:
    """Get an authorization header from the SDK."""
    sidecar_url = os.getenv('SIDECAR_URL', 'http://localhost:5000')
    
    response = requests.get(
        f"{sidecar_url}/AuthorizationHeader/{service_name}",
        headers={'Authorization': incoming_token}
    )
    
    if not response.ok:
        raise Exception(f"Failed to get authorization header: {response.text}")
    
    data = response.json()
    return data['authorizationHeader']

def get_user_profile(incoming_token: str) -> Dict[str, Any]:
    """Get user profile from Microsoft Graph."""
    # Get authorization header for Microsoft Graph
    auth_header = get_authorization_header(incoming_token, 'Graph')
    
    # Use the authorization header to call Microsoft Graph
    graph_response = requests.get(
        'https://graph.microsoft.com/v1.0/me',
        headers={'Authorization': auth_header}
    )
    
    if not graph_response.ok:
        raise Exception(f"Graph API error: {graph_response.text}")
    
    return graph_response.json()
```

If you want to integrate this function into a Flask application, you can use the following example:

```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/api/profile')
def profile():
    incoming_token = request.headers.get('Authorization')
    if not incoming_token:
        return jsonify({'error': 'No authorization token provided'}), 401
    
    try:
        profile_data = get_user_profile(incoming_token)
        return jsonify(profile_data)
    except Exception as e:
        print(f"Error fetching profile: {e}")
        return jsonify({'error': 'Failed to fetch profile'}), 500

if __name__ == '__main__':
    app.run(port=8080)
```

## Go

The following demonstrates a Go function to call the Microsoft Entra ID Auth SDK \(sidecar\) and obtain an authorization header. This implementation shows how to parse JSON responses and use the header:

```go
package main

import (
    "encoding/json"
    "fmt"
    "io"
    "net/http"
    "os"
)

type AuthHeaderResponse struct {
    AuthorizationHeader string `json:"authorizationHeader"`
}

type UserProfile struct {
    DisplayName string `json:"displayName"`
    Mail        string `json:"mail"`
    UserPrincipalName string `json:"userPrincipalName"`
}

func getAuthorizationHeader(incomingToken, serviceName string) (string, error) {
    sidecarURL := os.Getenv("SIDECAR_URL")
    if sidecarURL == "" {
        sidecarURL = "http://localhost:5000"
    }
    
    url := fmt.Sprintf("%s/AuthorizationHeader/%s", sidecarURL, serviceName)
    
    req, err := http.NewRequest("GET", url, nil)
    if err != nil {
        return "", err
    }
    
    req.Header.Set("Authorization", incomingToken)
    
    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        return "", err
    }
    defer resp.Body.Close()
    
    if resp.StatusCode != http.StatusOK {
        body, _ := io.ReadAll(resp.Body)
        return "", fmt.Errorf("failed to get authorization header: %s", string(body))
    }
    
    var authResp AuthHeaderResponse
    if err := json.NewDecoder(resp.Body).Decode(&authResp); err != nil {
        return "", err
    }
    
    return authResp.AuthorizationHeader, nil
}

func getUserProfile(incomingToken string) (*UserProfile, error) {
    // Get authorization header for Microsoft Graph
    authHeader, err := getAuthorizationHeader(incomingToken, "Graph")
    if err != nil {
        return nil, err
    }
    
    // Use the authorization header to call Microsoft Graph
    req, err := http.NewRequest("GET", "https://graph.microsoft.com/v1.0/me", nil)
    if err != nil {
        return nil, err
    }
    
    req.Header.Set("Authorization", authHeader)
    
    client := &http.Client{}
    resp, err := client.Do(req)
    if err != nil {
        return nil, err
    }
    defer resp.Body.Close()
    
    if resp.StatusCode != http.StatusOK {
        body, _ := io.ReadAll(resp.Body)
        return nil, fmt.Errorf("Graph API error: %s", string(body))
    }
    
    var profile UserProfile
    if err := json.NewDecoder(resp.Body).Decode(&profile); err != nil {
        return nil, err
    }
    
    return &profile, nil
}

// HTTP handler example
func profileHandler(w http.ResponseWriter, r *http.Request) {
    incomingToken := r.Header.Get("Authorization")
    if incomingToken == "" {
        http.Error(w, "No authorization token provided", http.StatusUnauthorized)
        return
    }
    
    profile, err := getUserProfile(incomingToken)
    if err != nil {
        fmt.Printf("Error fetching profile: %v\n", err)
        http.Error(w, "Failed to fetch profile", http.StatusInternalServerError)
        return
    }
    
    w.Header().Set("Content-Type", "application/json")
    json.NewEncoder(w).Encode(profile)
}

func main() {
    http.HandleFunc("/api/profile", profileHandler)
    fmt.Println("Server starting on :8080")
    http.ListenAndServe(":8080", nil)
}
```

## C# implementation

Create a C# class to call the Microsoft Entra ID Auth SDK \(sidecar\) and obtain an authorization header. This implementation uses ASP.NET Core's dependency injection:

```csharp
using System;
using System.Net.Http;
using System.Net.Http.Json;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;

public class SidecarClient
{
    private readonly HttpClient _httpClient;
    private readonly string _sidecarUrl;
    
    public SidecarClient(IHttpClientFactory httpClientFactory, IConfiguration config)
    {
        _httpClient = httpClientFactory.CreateClient();
        _sidecarUrl = config["SIDECAR_URL"] ?? "http://localhost:5000";
    }
    
    public async Task<string> GetAuthorizationHeaderAsync(
        string incomingAuthorizationHeader, 
        string serviceName)
    {
        var request = new HttpRequestMessage(
            HttpMethod.Get,
            $"{_sidecarUrl}/AuthorizationHeader/{serviceName}"
        );
        
        request.Headers.Add("Authorization", incomingAuthorizationHeader);
        
        var response = await _httpClient.SendAsync(request);
        response.EnsureSuccessStatusCode();
        
        var result = await response.Content.ReadFromJsonAsync<AuthHeaderResponse>();
        return result.AuthorizationHeader;
    }
}

public record AuthHeaderResponse(string AuthorizationHeader);

public record UserProfile(string DisplayName, string Mail, string UserPrincipalName);

// Controller example
[ApiController]
[Route("api/[controller]")]
public class ProfileController : ControllerBase
{
    private readonly SidecarClient _sidecarClient;
    private readonly HttpClient _httpClient;
    
    public ProfileController(SidecarClient sidecarClient, IHttpClientFactory httpClientFactory)
    {
        _sidecarClient = sidecarClient;
        _httpClient = httpClientFactory.CreateClient();
    }
    
    [HttpGet]
    public async Task<ActionResult<UserProfile>> GetProfile()
    {
        var incomingToken = Request.Headers["Authorization"].ToString();
        if (string.IsNullOrEmpty(incomingToken))
        {
            return Unauthorized("No authorization token provided");
        }
        
        try
        {
            // Get authorization header for Microsoft Graph
            var authHeader = await _sidecarClient.GetAuthorizationHeaderAsync(
                incomingToken, 
                "Graph"
            );
            
            // Use the authorization header to call Microsoft Graph
            var request = new HttpRequestMessage(
                HttpMethod.Get,
                "https://graph.microsoft.com/v1.0/me"
            );
            request.Headers.Add("Authorization", authHeader);
            
            var response = await _httpClient.SendAsync(request);
            response.EnsureSuccessStatusCode();
            
            var profile = await response.Content.ReadFromJsonAsync<UserProfile>();
            return Ok(profile);
        }
        catch (Exception ex)
        {
            return StatusCode(500, $"Failed to fetch profile: {ex.Message}");
        }
    }
}
```

## Advanced scenarios

The Microsoft Entra ID Auth SDK \(sidecar\) supports several advanced patterns through query parameters:

### Override scopes

Request specific scopes different from configuration:

```typescript
const response = await fetch(
  `${sidecarUrl}/AuthorizationHeader/Graph?` +
  `optionsOverride.Scopes=User.Read&` +
  `optionsOverride.Scopes=Mail.Send`,
  {
    headers: { 'Authorization': incomingToken }
  }
);
```

### Multi-tenant support

Override tenant for specific user:

```typescript
const response = await fetch(
  `${sidecarUrl}/AuthorizationHeader/Graph?` +
  `optionsOverride.AcquireTokenOptions.Tenant=${userTenantId}`,
  {
    headers: { 'Authorization': incomingToken }
  }
);
```

### Request application token

Request an application token instead of OBO:

```typescript
const response = await fetch(
  `${sidecarUrl}/AuthorizationHeader/Graph?` +
  `optionsOverride.RequestAppToken=true`,
  {
    headers: { 'Authorization': incomingToken }
  }
);
```

### With agent identity

Use agent identity for delegation:

```typescript
const response = await fetch(
  `${sidecarUrl}/AuthorizationHeader/Graph?` +
  `AgentIdentity=${agentClientId}&` +
  `AgentUsername=${encodeURIComponent(userPrincipalName)}`,
  {
    headers: { 'Authorization': incomingToken }
  }
);
```

## Error handling

Implement proper error handling when calling the Microsoft Entra ID Auth SDK \(sidecar\) to distinguish between transient and permanent failures:

### Handle transient errors

Implement retry logic with exponential backoff for transient failures:

```typescript
async function getAuthorizationHeaderWithRetry(
  incomingToken: string,
  serviceName: string,
  maxRetries = 3
): Promise<string> {
  let lastError: Error;
  
  for (let attempt = 1; attempt <= maxRetries; attempt++) {
    try {
      const response = await fetch(
        `${sidecarUrl}/AuthorizationHeader/${serviceName}`,
        {
          headers: { 'Authorization': incomingToken }
        }
      );
      
      if (response.ok) {
        const data = await response.json();
        return data.authorizationHeader;
      }
      
      // Don't retry on 4xx errors (client errors)
      if (response.status >= 400 && response.status < 500) {
        const error = await response.json();
        throw new Error(`Client error: ${error.detail || response.statusText}`);
      }
      
      // Retry on 5xx errors (server errors)
      lastError = new Error(`Server error: ${response.statusText}`);
      
      if (attempt < maxRetries) {
        // Exponential backoff
        await new Promise(resolve => 
          setTimeout(resolve, Math.pow(2, attempt) * 100)
        );
      }
    } catch (error) {
      lastError = error as Error;
      if (attempt < maxRetries) {
        await new Promise(resolve => 
          setTimeout(resolve, Math.pow(2, attempt) * 100)
        );
      }
    }
  }
  
  throw new Error(`Failed after ${maxRetries} retries: ${lastError.message}`);
}
```

## Best practices

When obtaining authorization headers from the Microsoft Entra ID Auth SDK \(sidecar\), follow these practices:

- **Reuse HTTP Clients**: Create a single HTTP client instance and reuse it across requests rather than creating new clients per call. This improves performance and enables connection pooling.
- **Handle Errors Gracefully**: Implement retry logic for transient failures \(5xx errors\) but fail immediately on client errors \(4xx responses\) that indicate configuration problems.
- **Set Appropriate Timeouts**: Configure timeouts for SDK calls based on expected latency. This prevents your application from hanging if the SDK is unresponsive.
- **Cache Authorization Headers**: Cache returned headers for their lifetime to reduce unnecessary calls to the SDK. Respect the token's expiration time when caching.
- **Log Correlation IDs**: Include correlation IDs from SDK responses in your logs to enable request tracing across system boundaries.
- **Validate Responses**: Always check response status codes and validate that required fields are present before using the authorization header.

## Related content

- [Call a downstream API](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/call-downstream-api)
- [Validate an authorization header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/validate-authorization-header)
- [Using from TypeScript](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-typescript)
- [Using from Python](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-python)
