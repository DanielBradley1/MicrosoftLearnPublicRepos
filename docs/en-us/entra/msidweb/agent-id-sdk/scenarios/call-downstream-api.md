<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/call-downstream-api -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Scenario: Call a downstream API

Use the Microsoft Entra ID Auth SDK \(sidecar\) to handle both token acquisition and HTTP communication in a single operation. The SDK exchanges your incoming token for one scoped to the downstream API, then makes the HTTP call and returns the response. This guide shows you how to configure downstream APIs, implement calls in TypeScript and Python, handle different HTTP methods, and manage errors with retries.

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- **Microsoft Entra ID Auth SDK \(sidecar\)** deployed and running in your environment. See [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation) for setup instructions.
- **Downstream API configured** in the SDK with the base URL and required scopes for the APIs you want to call.
- **Bearer tokens from authenticated clients** - Your application receives tokens from client applications that you'll forward to the SDK.
- **Appropriate permissions in Microsoft Entra ID** - Your account must have permissions to register applications and grant API permissions.

## Configuration

Configure the downstream API in your Microsoft Entra ID Auth SDK \(sidecar\) environment settings:

```yaml
env:
- name: DownstreamApis__Graph__BaseUrl
  value: "https://graph.microsoft.com/v1.0"
- name: DownstreamApis__Graph__Scopes__0
  value: "User.Read"
- name: DownstreamApis__Graph__Scopes__1
  value: "Mail.Read"
```

The configuration specifies:

- **BaseUrl**: The root endpoint of your downstream API
- **Scopes**: The permissions required for accessing the downstream API

## TypeScript/Node.js

The following examples show how to call downstream APIs from TypeScript and Node.js applications. The code demonstrates both a reusable function and integration with Express.js.

```typescript
interface DownstreamApiResponse {
  statusCode: number;
  headers: Record<string, string>;
  content: string;
}

async function callDownstreamApi(
  incomingToken: string,
  serviceName: string,
  relativePath: string,
  method: string = 'GET',
  body?: any
): Promise<any> {
  const sdkUrl = process.env.ENTRA_SDK_URL || 'http://localhost:5000';
  
  const url = new URL(`${sdkUrl}/DownstreamApi/${serviceName}`);
  url.searchParams.append('optionsOverride.RelativePath', relativePath);
  if (method !== 'GET') {
    url.searchParams.append('optionsOverride.HttpMethod', method);
  }
  
  const requestOptions: any = {
    method: method,
    headers: {
      'Authorization': incomingToken
    }
  };
  
  if (body) {
    requestOptions.headers['Content-Type'] = 'application/json';
    requestOptions.body = JSON.stringify(body);
  }
  
  const response = await fetch(url.toString(), requestOptions);
  
  if (!response.ok) {
    throw new Error(`SDK error: ${response.statusText}`);
  }
  
  const data = await response.json() as DownstreamApiResponse;
  
  if (data.statusCode >= 400) {
    throw new Error(`API error ${data.statusCode}: ${data.content}`);
  }
  
  return JSON.parse(data.content);
}

// Usage examples
async function getUserProfile(incomingToken: string) {
  return await callDownstreamApi(incomingToken, 'Graph', 'me');
}

async function listEmails(incomingToken: string) {
  return await callDownstreamApi(
    incomingToken,
    'Graph',
    'me/messages?$top=10&$select=subject,from,receivedDateTime'
  );
}

async function sendEmail(incomingToken: string, message: any) {
  return await callDownstreamApi(
    incomingToken,
    'Graph',
    'me/sendMail',
    'POST',
    { message }
  );
}
```

The following example demonstrates how to integrate these functions into an Express.js application using middleware and route handlers:

```javascript
// Express.js API example
import express from 'express';

const app = express();
app.use(express.json());

app.get('/api/profile', async (req, res) => {
  try {
    const incomingToken = req.headers.authorization;
    if (!incomingToken) {
      return res.status(401).json({ error: 'No authorization token' });
    }
    
    const profile = await getUserProfile(incomingToken);
    res.json(profile);
  } catch (error) {
    console.error('Error:', error);
    res.status(500).json({ error: 'Failed to fetch profile' });
  }
});

app.get('/api/messages', async (req, res) => {
  try {
    const incomingToken = req.headers.authorization;
    if (!incomingToken) {
      return res.status(401).json({ error: 'No authorization token' });
    }
    
    const messages = await listEmails(incomingToken);
    res.json(messages);
  } catch (error) {
    console.error('Error:', error);
    res.status(500).json({ error: 'Failed to fetch messages' });
  }
});

app.post('/api/messages/send', async (req, res) => {
  try {
    const incomingToken = req.headers.authorization;
    if (!incomingToken) {
      return res.status(401).json({ error: 'No authorization token' });
    }
    
    const message = req.body;
    await sendEmail(incomingToken, message);
    res.json({ success: true });
  } catch (error) {
    console.error('Error:', error);
    res.status(500).json({ error: 'Failed to send message' });
  }
});

app.listen(8080, () => {
  console.log('Server running on port 8080');
});
```

## Python

The following examples show how to call downstream APIs from Python applications using the requests library and Flask for HTTP handling:

```python
import os
import json
import requests
from typing import Dict, Any, Optional

def call_downstream_api(
    incoming_token: str,
    service_name: str,
    relative_path: str,
    method: str = 'GET',
    body: Optional[Dict[str, Any]] = None
) -> Any:
    """Call a downstream API via the Microsoft Entra ID Auth SDK (sidecar)."""
    sdk_url = os.getenv('ENTRA_SDK_URL', 'http://localhost:5000')
    
    params = {
        'optionsOverride.RelativePath': relative_path
    }
    
    if method != 'GET':
        params['optionsOverride.HttpMethod'] = method
    
    headers = {'Authorization': incoming_token}
    json_body = None
    
    if body:
        headers['Content-Type'] = 'application/json'
        json_body = body
    
    response = requests.request(
        method,
        f"{sdk_url}/DownstreamApi/{service_name}",
        params=params,
        headers=headers,
        json=json_body
    )
    
    if not response.ok:
        raise Exception(f"SDK error: {response.text}")
    
    data = response.json()
    
    if data['statusCode'] >= 400:
        raise Exception(f"API error {data['statusCode']}: {data['content']}")
    
    return json.loads(data['content'])

# Usage examples
def get_user_profile(incoming_token: str) -> Dict[str, Any]:
    return call_downstream_api(incoming_token, 'Graph', 'me')

def list_emails(incoming_token: str) -> Dict[str, Any]:
    return call_downstream_api(
        incoming_token,
        'Graph',
        'me/messages?$top=10&$select=subject,from,receivedDateTime'
    )

def send_email(incoming_token: str, message: Dict[str, Any]) -> None:
    call_downstream_api(
        incoming_token,
        'Graph',
        'me/sendMail',
        'POST',
        {'message': message}
    )
```

If you want to integrate these functions into a Flask application, you can use the following example:

```python
# Flask API example
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/api/profile')
def profile():
    incoming_token = request.headers.get('Authorization')
    if not incoming_token:
        return jsonify({'error': 'No authorization token'}), 401
    
    try:
        profile_data = get_user_profile(incoming_token)
        return jsonify(profile_data)
    except Exception as e:
        print(f"Error: {e}")
        return jsonify({'error': 'Failed to fetch profile'}), 500

@app.route('/api/messages')
def messages():
    incoming_token = request.headers.get('Authorization')
    if not incoming_token:
        return jsonify({'error': 'No authorization token'}), 401
    
    try:
        messages_data = list_emails(incoming_token)
        return jsonify(messages_data)
    except Exception as e:
        print(f"Error: {e}")
        return jsonify({'error': 'Failed to fetch messages'}), 500

@app.route('/api/messages/send', methods=['POST'])
def send_message():
    incoming_token = request.headers.get('Authorization')
    if not incoming_token:
        return jsonify({'error': 'No authorization token'}), 401
    
    try:
        message = request.json
        send_email(incoming_token, message)
        return jsonify({'success': True})
    except Exception as e:
        print(f"Error: {e}")
        return jsonify({'error': 'Failed to send message'}), 500

if __name__ == '__main__':
    app.run(port=8080)
```

## POST/PUT/PATCH requests

The `/DownstreamApi` endpoint supports modification operations by passing the HTTP method and request body. Use these patterns when you need to create, update, or delete resources in the downstream API.

### Creating resources

```typescript
// POST example - Create a calendar event
async function createEvent(incomingToken: string, event: any) {
  return await callDownstreamApi(
    incomingToken,
    'Graph',
    'me/events',
    'POST',
    event
  );
}

// Usage
const newEvent = {
  subject: "Team Meeting",
  start: {
    dateTime: "2024-01-15T14:00:00",
    timeZone: "Pacific Standard Time"
  },
  end: {
    dateTime: "2024-01-15T15:00:00",
    timeZone: "Pacific Standard Time"
  }
};

const createdEvent = await createEvent(incomingToken, newEvent);
```

### Updating resources

```typescript
// PATCH example - Update user profile
async function updateProfile(incomingToken: string, updates: any) {
  return await callDownstreamApi(
    incomingToken,
    'Graph',
    'me',
    'PATCH',
    updates
  );
}

// Usage
await updateProfile(incomingToken, {
  mobilePhone: "+1 555 0100",
  officeLocation: "Building 2, Room 201"
});
```

## Advanced scenarios

The following scenarios demonstrate advanced configurations for specialized use cases.

### Custom headers

Add custom headers to the downstream API request:

```typescript
const url = new URL(`${sdkUrl}/DownstreamApi/MyApi`);
url.searchParams.append('optionsOverride.RelativePath', 'items');
url.searchParams.append('optionsOverride.CustomHeader.X-Custom-Header', 'custom-value');
url.searchParams.append('optionsOverride.CustomHeader.X-Request-Id', requestId);
```

### Override scopes

Request different scopes than the default configured scopes:

```typescript
const url = new URL(`${sdkUrl}/DownstreamApi/Graph`);
url.searchParams.append('optionsOverride.RelativePath', 'me');
url.searchParams.append('optionsOverride.Scopes', 'User.ReadWrite');
url.searchParams.append('optionsOverride.Scopes', 'Mail.Send');
```

### With agent identity

Use agent identity to call APIs with application permissions:

```typescript
const url = new URL(`${sdkUrl}/DownstreamApi/Graph`);
url.searchParams.append('optionsOverride.RelativePath', 'users');
url.searchParams.append('AgentIdentity', agentClientId);
url.searchParams.append('AgentUsername', 'admin@contoso.com');
```

## Error handling

Implement retry logic with exponential backoff to handle transient failures gracefully:

```typescript
async function callDownstreamApiWithRetry(
  incomingToken: string,
  serviceName: string,
  relativePath: string,
  method: string = 'GET',
  body?: any,
  maxRetries: number = 3
): Promise<any> {
  let lastError: Error;
  
  for (let attempt = 1; attempt <= maxRetries; attempt++) {
    try {
      return await callDownstreamApi(
        incomingToken,
        serviceName,
        relativePath,
        method,
        body
      );
    } catch (error) {
      lastError = error as Error;
      
      // Don't retry on client errors (4xx)
      if (error.message.includes('API error 4')) {
        throw error;
      }
      
      // Retry on server errors (5xx) or network errors
      if (attempt < maxRetries) {
        const delay = Math.pow(2, attempt) * 100;
        await new Promise(resolve => setTimeout(resolve, delay));
      }
    }
  }
  
  throw new Error(`Failed after ${maxRetries} retries: ${lastError!.message}`);
}
```

## Comparison with AuthorizationHeader approach

The Microsoft Entra ID Auth SDK \(sidecar\) provides two approaches for calling downstream APIs. Use this comparison to determine which approach best fits your needs.

### Capabilities comparison

| Capability | /DownstreamApi | /AuthorizationHeader |
| --- | --- | --- |
| Token Acquisition | Handled by SDK | Handled by SDK |
| HTTP Request | Handled by SDK | Your responsibility |
| Response Parsing | Wrapped in JSON | Direct HTTP response |
| Custom Headers | Via query parameters | Full HTTP control |
| Request Body | Forwarded automatically | Full control |
| Error Handling | SDK-wrapped errors | Standard HTTP errors |

### When to use each approach

| Use Case | Recommendation | Best For |
| --- | --- | --- |
| Standard REST API calls with conventional patterns | `/DownstreamApi` | GET, POST, PUT, PATCH, DELETE operations; reducing boilerplate |
| Complex HTTP clients requiring custom configuration | `/AuthorizationHeader` | Specialized request/response handling; fine-grained control |
| Direct access to HTTP error codes and headers needed | `/AuthorizationHeader` | Applications needing low-level HTTP behavior control |
| Simplicity and quick integration prioritized | `/DownstreamApi` | Applications prioritizing simplicity over low-level control |

## Best practices

1. **Reuse HTTP clients**: Create once and reuse to avoid connection overhead
2. **Implement error handling**: Add retry logic for transient failures with exponential backoff
3. **Check status codes**: Always verify the status code before parsing response content
4. **Set timeouts**: Configure appropriate request timeouts to prevent hanging requests
5. **Include correlation IDs**: Log all requests with unique identifiers for end-to-end tracing
6. **Validate input**: Sanitize and validate data before sending to downstream APIs
7. **Monitor performance**: Track API call latency and failure rates for observability

## Related content

- [Obtain an authorization header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/obtain-authorization-header)
- [Using from TypeScript](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-typescript)
- [Using from Python](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-python)
- [Security](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)
