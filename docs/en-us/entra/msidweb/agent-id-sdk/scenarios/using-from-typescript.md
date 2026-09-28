<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-typescript -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Scenario: Using the Microsoft Entra ID Auth SDK \(sidecar\) from TypeScript

Create a TypeScript/Node.js client library that integrates with the Microsoft Entra ID Auth SDK \(sidecar\) to obtain tokens and call downstream APIs. Then integrate this client into Express.js or NestJS applications to handle authenticated API requests.

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- **Node.js** \(version 14 or later\) with npm installed on your development machine.
- **Microsoft Entra ID Auth SDK \(sidecar\)** deployed and running in your environment. See [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation) for setup instructions.
- **Downstream APIs configured** in the SDK with base URLs and required scopes.
- **Appropriate permissions in Microsoft Entra ID** - Your account must have permissions to register applications and grant API permissions.

## Setup

Before creating your client library, install the required dependencies for making HTTP requests:

```bash
npm install node-fetch
npm install --save-dev @types/node-fetch
```

## Client library implementation

Create a reusable client class that wraps HTTP calls to the Microsoft Entra ID Auth SDK \(sidecar\). This class handles token forwarding, request configuration, and error handling:

```typescript
// sidecar-client.ts
import fetch from 'node-fetch';

export interface SidecarConfig {
  baseUrl: string;
  timeout?: number;
}

export class SidecarClient {
  private readonly baseUrl: string;
  private readonly timeout: number;
  
  constructor(config: SidecarConfig) {
    this.baseUrl = config.baseUrl || process.env.SIDECAR_URL || 'http://localhost:5000';
    this.timeout = config.timeout || 10000;
  }
  
  async getAuthorizationHeader(
    incomingToken: string,
    serviceName: string,
    options?: {
      scopes?: string[];
      tenant?: string;
      agentIdentity?: string;
      agentUsername?: string;
    }
  ): Promise<string> {
    const url = new URL(`${this.baseUrl}/AuthorizationHeader/${serviceName}`);
    
    if (options?.scopes) {
      options.scopes.forEach(scope => 
        url.searchParams.append('optionsOverride.Scopes', scope)
      );
    }
    
    if (options?.tenant) {
      url.searchParams.append('optionsOverride.AcquireTokenOptions.Tenant', options.tenant);
    }
    
    if (options?.agentIdentity) {
      url.searchParams.append('AgentIdentity', options.agentIdentity);
      if (options.agentUsername) {
        url.searchParams.append('AgentUsername', options.agentUsername);
      }
    }
    
    const response = await fetch(url.toString(), {
      headers: { 'Authorization': incomingToken },
      signal: AbortSignal.timeout(this.timeout)
    });
    
    if (!response.ok) {
      throw new Error(`SDK error: ${response.statusText}`);
    }
    
    const data = await response.json();
    return data.authorizationHeader;
  }
  
  async callDownstreamApi<T>(
    incomingToken: string,
    serviceName: string,
    relativePath: string,
    options?: {
      method?: string;
      body?: any;
      scopes?: string[];
    }
  ): Promise<T> {
    const url = new URL(`${this.baseUrl}/DownstreamApi/${serviceName}`);
    url.searchParams.append('optionsOverride.RelativePath', relativePath);
    
    if (options?.method && options.method !== 'GET') {
      url.searchParams.append('optionsOverride.HttpMethod', options.method);
    }
    
    if (options?.scopes) {
      options.scopes.forEach(scope => 
        url.searchParams.append('optionsOverride.Scopes', scope)
      );
    }
    
    const fetchOptions: any = {
      method: options?.method || 'GET',
      headers: { 'Authorization': incomingToken },
      signal: AbortSignal.timeout(this.timeout)
    };
    
    if (options?.body) {
      fetchOptions.headers['Content-Type'] = 'application/json';
      fetchOptions.body = JSON.stringify(options.body);
    }
    
    const response = await fetch(url.toString(), fetchOptions);
    
    if (!response.ok) {
      throw new Error(`SDK error: ${response.statusText}`);
    }
    
    const data = await response.json();
    
    if (data.statusCode >= 400) {
      throw new Error(`API error ${data.statusCode}: ${data.content}`);
    }
    
    return JSON.parse(data.content) as T;
  }
}

// Usage
const sidecar = new SidecarClient({ baseUrl: 'http://localhost:5000' });

// Get authorization header
const authHeader = await sidecar.getAuthorizationHeader(token, 'Graph');

// Call API
interface UserProfile {
  displayName: string;
  mail: string;
  userPrincipalName: string;
}

const profile = await sidecar.callDownstreamApi<UserProfile>(
  token,
  'Graph',
  'me'
);
```

## Express.js integration

Integrate the client library into an Express.js application by creating middleware to extract the incoming token and route handlers that call downstream APIs:

```typescript
import express from 'express';
import { SidecarClient } from './sidecar-client';

const app = express();
app.use(express.json());

const sidecar = new SidecarClient({ baseUrl: process.env.SIDECAR_URL! });

// Middleware to extract token
app.use((req, res, next) => {
  const token = req.headers.authorization;
  if (!token && !req.path.startsWith('/health')) {
    return res.status(401).json({ error: 'No authorization token' });
  }
  req.userToken = token;
  next();
});

// Routes
app.get('/api/profile', async (req, res) => {
  try {
    const profile = await sidecar.callDownstreamApi(
      req.userToken,
      'Graph',
      'me'
    );
    res.json(profile);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

app.get('/api/messages', async (req, res) => {
  try {
    const messages = await sidecar.callDownstreamApi(
      req.userToken,
      'Graph',
      'me/messages?$top=10'
    );
    res.json(messages);
  } catch (error) {
    res.status(500).json({ error: error.message });
  }
});

app.listen(8080, () => {
  console.log('Server running on port 8080');
});
```

## NestJS integration

For NestJS applications, create a service that wraps the client library. This service can be injected into controllers to handle authenticated requests:

```typescript
import { Injectable } from '@nestjs/common';
import { SidecarClient } from './sidecar-client';

@Injectable()
export class GraphService {
  private readonly sidecar: SidecarClient;
  
  constructor() {
    this.sidecar = new SidecarClient({ 
      baseUrl: process.env.SIDECAR_URL! 
    });
  }
  
  async getUserProfile(token: string) {
    return await this.sidecar.callDownstreamApi(
      token,
      'Graph',
      'me'
    );
  }
  
  async getUserMessages(token: string, top: number = 10) {
    return await this.sidecar.callDownstreamApi(
      token,
      'Graph',
      `me/messages?$top=${top}`
    );
  }
}
```

## Best practices

When using the Microsoft Entra ID Auth SDK \(sidecar\) from TypeScript, follow these practices to build reliable and maintainable applications:

- **Reuse Client Instance**: Create a single `SidecarClient` instance and reuse it throughout your application rather than creating new instances per request. This improves performance and resource usage.
- **Set Appropriate Timeouts**: Configure request timeouts based on your downstream API latency. This prevents your application from hanging indefinitely if the SDK or downstream service is slow.
- **Implement Error Handling**: Add proper error handling and retry logic, especially for transient failures. Distinguish between client errors \(4xx\) and server errors \(5xx\) to determine appropriate responses.
- **Use TypeScript Interfaces**: Define TypeScript interfaces for API responses to ensure type safety and catch errors at compile time rather than runtime.
- **Enable Connection Pooling**: Use HTTP agents to enable connection reuse across requests, which reduces overhead and improves throughput.

## Related content

- [Call a downstream API](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/call-downstream-api)
- [Obtain an authorization header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/obtain-authorization-header)
- [Validate an authorization header](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/validate-authorization-header)
- [Using from Python](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-python)
