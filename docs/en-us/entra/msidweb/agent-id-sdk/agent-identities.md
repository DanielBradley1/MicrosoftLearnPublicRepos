<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/agent-identities -->
<!-- Sitemap-Last-Modified: 2026-04-19 -->

# Agent identities: autonomous and interactive agent patterns

Agent identities enable sophisticated authentication scenarios where an agent application acts autonomously or on behalf of users. By using agent identities with the Microsoft Entra ID Auth SDK \(sidecar\), you can create both autonomous agents that operate in their own context and interactive agents that act on behalf of users. To facilitate these scenarios, the SDK supports specific query parameters to specify agent identities and user contexts.

For detailed guidance on agent identities, see the [Microsoft agent identity platform documentation](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform).

## Overview

Agent identities support two primary patterns:

- **Autonomous Agent**: The agent operates in its own application context.
- **Interactive Agent**: An interactive agent operates on behalf of a user.

The SDK accepts three optional query parameters:

- `AgentIdentity` - GUID of the agent identity.
- `AgentUsername` - User principal name \(UPN\) for specific user.
- `AgentUserId` - User object ID \(OID\) for specific user, as an alternative to UPN.

## Precedence rules

`AgentUsername` and `AgentUserId` are mutually exclusive. Requests that include both parameters fail validation, as described in [Rule 2: mutual exclusivity](#rule-2-mutual-exclusivity). Provide only one of these parameters per request.

## Microsoft Entra ID configuration

Before configuring agent identities in your application, set up the necessary components in Microsoft Entra ID. To register a new application in Microsoft Entra ID tenant, see [Register an application](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp).

### Prerequisites for agent identities

1. **Agent application registration**:

   - Register the parent agent application in Microsoft Entra ID.
   - Configure API permissions for downstream APIs.
   - Set up client credentials \(FIC+MSI, certificate, or secret\).

2. **Agent identity configuration**:

   - Create agent identities by using the agent blueprint.
   - Assign necessary permissions to agent identities.

3. **Application permissions**:

   - Grant application permissions for autonomous scenarios.
   - Grant delegated permissions for user delegation scenarios.
   - Ensure admin consent is provided where required.

For detailed step-by-step instructions on configuring agent identities in Microsoft Entra ID, see the [Microsoft agent identity platform documentation](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform).

## Semantic rules

To authenticate successfully, you must use agent identity parameters correctly. The following rules govern the use of `AgentIdentity`, `AgentUsername`, and `AgentUserId` parameters. Follow these rules to avoid validation errors that the SDK returns.

### Rule 1: AgentIdentity requirement

**`AgentUsername`** or **`AgentUserId`** must be paired with **`AgentIdentity`**.

If you specify `AgentUsername` or `AgentUserId` without `AgentIdentity`, the request fails with a validation error.

```bash
# INVALID - AgentUsername without AgentIdentity
GET /AuthorizationHeader/Graph?AgentUsername=user@contoso.com

# VALID - AgentUsername with AgentIdentity
GET /AuthorizationHeader/Graph?AgentIdentity=agent-client-id&AgentUsername=user@contoso.com
```

### Rule 2: Mutual exclusivity

**`AgentUsername`** and **`AgentUserId`** are mutually exclusive parameters.

You can't specify both `AgentUsername` and `AgentUserId` in the same request. If you provide both parameters, the request fails with a validation error.

```bash
# INVALID - Both AgentUsername and AgentUserId specified
GET /AuthorizationHeader/Graph?AgentIdentity=agent-id&AgentUsername=user@contoso.com&AgentUserId=user-oid

# VALID - Only AgentUsername
GET /AuthorizationHeader/Graph?AgentIdentity=agent-id&AgentUsername=user@contoso.com

# VALID - Only AgentUserId
GET /AuthorizationHeader/Graph?AgentIdentity=agent-id&AgentUserId=user-object-id
```

### Rule 3: Autonomous vs interactive

The combination of parameters determines the authentication pattern:

| Parameters | Pattern | Description |
| --- | --- | --- |
| `AgentIdentity` only | **Autonomous Agent** | Acquires application token for the agent identity |
| `AgentIdentity` + `AgentUsername` | **Interactive Agent** | Acquires user token for the specified user \(by UPN\) |
| `AgentIdentity` + `AgentUserId` | **Interactive Agent** | Acquires user token for the specified user \(by Object ID\) |

**Examples**:

```bash
# Autonomous agent - application context
GET /AuthorizationHeader/Graph?AgentIdentity=agent-id

# Interactive agent - user context by username
GET /AuthorizationHeader/Graph?AgentIdentity=agent-id&AgentUsername=user@contoso.com

# Interactive agent - user context by user ID
GET /AuthorizationHeader/Graph?AgentIdentity=agent-id&AgentUserId=user-object-id
```

## Usage patterns

For each usage pattern, the combination of parameters determines the authentication flow and the type of token acquired.

### Pattern 1: Autonomous agent

The agent application runs independently in its own application context and gets application tokens.

**Scenario**: A batch processing service that processes files on its own.

```bash
GET /AuthorizationHeader/Graph?AgentIdentity=12345678-1234-1234-1234-123456789012
```

**Token characteristics**:

- Token type: Application token
- Subject \(`sub`\): Agent application's object ID
- Token created for the agent's identity
- **Permissions**: Application permissions assigned to agent identity

**Use cases**:

- Automated batch processing
- Background tasks
- System-to-system operations
- Scheduled jobs without user context

### Pattern 2: Autonomous user agent \(by username\)

The agent runs on behalf of a specific user identified by their UPN.

**Scenario**: An AI assistant that acts on behalf of a user in a chat application.

```bash
GET /AuthorizationHeader/Graph?AgentIdentity=12345678-1234-1234-1234-123456789012&AgentUsername=alice@contoso.com
```

**Token characteristics**:

- Token type: User token
- Subject \(`sub`\): User's Object ID
- Agent identity facet included in token claims
- **Permissions**: Interactive permissions scoped to user

**Use cases**:

- Interactive agent applications
- AI assistants with user delegation
- User-scoped automation
- Personalized workflows

### Pattern 3: Autonomous user agent \(by Object ID\)

The agent works on behalf of a specific user identified by their Object ID.

**Scenario**: A workflow engine that processes user-specific tasks by using stored user IDs.

```bash
GET /AuthorizationHeader/Graph?AgentIdentity=12345678-1234-1234-1234-123456789012&AgentUserId=87654321-4321-4321-4321-210987654321
```

**Token characteristics**:

- Token type: User token
- Subject \(`sub`\): User's Object ID
- Agent identity facet included in token claims
- **Permissions**: Interactive permissions scoped to user

**Use cases**:

- Long-running workflows with stored user identifiers
- Batch operations on behalf of multiple users
- Systems that use Object IDs for user reference

### Pattern 4: Interactive agent \(acting on behalf of the user calling it\)

An agent web API receives a user token, validates it, and makes delegated calls on behalf of that user.

**Scenario**: A web API acting as an interactive agent validating incoming user tokens and making delegated calls to downstream services.

**Flow**:

1. Agent web API receives user token from the calling application.
2. Validates token via the `/Validate` endpoint.
3. Acquires tokens for downstream APIs by calling `/AuthorizationHeader` with only the `AgentIdentity` and the incoming Authorization header.

```bash
# Step 1: Validate incoming user token
GET /Validate
Authorization: Bearer <user-token>

# Step 2: Get authorization header on behalf of the user
GET /AuthorizationHeader/Graph?AgentIdentity=<agent-client-id>
Authorization: Bearer <user-token>
```

**Token characteristics**:

- Token type: User token \(OBO flow\)
- Subject \(`sub`\): Original user's Object ID
- Agent acts as intermediary for user
- **Permissions**: Interactive permissions scoped to the user

**Use cases**:

- Web APIs that act as agents
- Interactive agent services
- Agent-based middleware that delegates to downstream APIs
- Services that validate and forward user context

### Pattern 5: Regular request \(no agent\)

When you don't provide agent parameters, the SDK uses the incoming token's identity.

**Scenario**: Standard on-behalf-of \(OBO\) flow without agent identities.

```bash
GET /AuthorizationHeader/Graph
Authorization: Bearer <user-token>
```

**Token characteristics**:

- Token type: Depends on incoming token and configuration
- Uses standard OBO or client credentials flow
- No agent identity facets

## Code examples

The following code snippets demonstrate how to implement the different agent identity patterns using various programming languages, and how to interact with the SDK endpoints. The code demonstrates how to handle out of process calls to the SDK to acquire authorization headers for downstream API calls.

### TypeScript: Autonomous agent

```typescript
const sidecarUrl = "http://localhost:5000";
const Agent ID = "12345678-1234-1234-1234-123456789012";

async function runBatchJob() {
  const response = await fetch(
    `${sidecarUrl}/AuthorizationHeader/Graph?AgentIdentity=${agentId}`,
    {
      headers: {
        'Authorization': 'Bearer system-token'
      }
    }
  );
  
  const { authorizationHeader } = await response.json();
  // Use authorizationHeader for downstream API calls
}
```

### Python: Agent with user identity

```python
import requests

sidecar_url = "http://localhost:5000"
agent_id = "12345678-1234-1234-1234-123456789012"
user_email = "alice@contoso.com"

response = requests.get(
    f"{sidecar_url}/AuthorizationHeader/Graph",
    params={
        "AgentIdentity": agent_id,
        "AgentUsername": user_email
    },
    headers={"Authorization": f"Bearer {system_token}"}
)

token = response.json()["authorizationHeader"]
```

### TypeScript: Interactive agent

```typescript
async function delegateCall(userToken: string) {
  // Validate incoming token
  const validation = await fetch(
    `${sidecarUrl}/Validate`,
    {
      headers: { 'Authorization': `Bearer ${userToken}` }
    }
  );
  
  const claims = await validation.json();
  
  // Call downstream API on behalf of user
  const response = await fetch(
    `${sidecarUrl}/DownstreamApi/Graph`,
    {
      headers: { 'Authorization': `Bearer ${userToken}` }
    }
  );
  
  return await response.json();
}
```

### C# with HttpClient

```csharp
using System.Net.Http;

var httpClient = new HttpClient();

// Autonomous agent
var autonomousUrl = $"http://localhost:5000/AuthorizationHeader/Graph" +
    $"?AgentIdentity={agentClientId}";
var response = await httpClient.GetAsync(autonomousUrl);

// Delegated agent with username
var delegatedUrl = $"http://localhost:5000/AuthorizationHeader/Graph" +
    $"?AgentIdentity={agentClientId}" +
    $"&AgentUsername={Uri.EscapeDataString(userPrincipalName)}";
response = await httpClient.GetAsync(delegatedUrl);

// Delegated agent with user ID
var delegatedByIdUrl = $"http://localhost:5000/AuthorizationHeader/Graph" +
    $"?AgentIdentity={agentClientId}" +
    $"&AgentUserId={userObjectId}";
response = await httpClient.GetAsync(delegatedByIdUrl);
```

## Error scenarios

When you misconfigure agent identity parameters or use them incorrectly, the SDK returns validation errors. The following sections describe common error scenarios and their corresponding responses. For more details on error handling, see the [Troubleshooting Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/troubleshooting).

### Missing AgentIdentity with AgentUsername

**Request**:

```bash
GET /AuthorizationHeader/Graph?AgentUsername=user@contoso.com
```

**Response**:

```json
{
  "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
  "title": "Bad Request",
  "status": 400,
  "detail": "AgentUsername requires AgentIdentity to be specified"
}
```

### Both AgentUsername and AgentUserId specified

**Request**:

```bash
GET /AuthorizationHeader/Graph?AgentIdentity=agent-id&AgentUsername=user@contoso.com&AgentUserId=user-oid
```

**Response**:

```json
{
  "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
  "title": "Bad Request",
  "status": 400,
  "detail": "AgentUsername and AgentUserId are mutually exclusive"
}
```

### Invalid AgentUserId format

**Request**:

```bash
GET /AuthorizationHeader/Graph?AgentIdentity=agent-id&AgentUserId=invalid-guid
```

**Response**:

```json
{
  "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
  "title": "Bad Request",
  "status": 400,
  "detail": "AgentUserId must be a valid GUID"
}
```

## Best practices

1. **Validate input**: Always validate agent identity parameters before making requests.
2. **Use object IDs when available**: Object IDs are more stable.
3. **Implement proper error handling**: Handle agent identity validation errors gracefully.
4. **Secure agent credentials**: Protect agent identity client IDs and credentials.
5. **Audit agent operations**: Log and monitor agent identity usage for security and compliance.
6. **Test both patterns**: Validate both autonomous and delegated scenarios in your tests.
7. **Document intent**: Clearly document which agent pattern is appropriate for each use case.

## Related content

- [Endpoints Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/endpoints)
- [Configuration Reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
- [Scenario: Agent Autonomous Batch Processing](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/agent-autonomous-batch)
- [Microsoft agent identity platform](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform)
