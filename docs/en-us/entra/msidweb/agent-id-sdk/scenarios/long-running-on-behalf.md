<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/long-running-on-behalf -->
<!-- Sitemap-Last-Modified: 2026-04-19 -->

# Scenario: Long-Running on-behalf-of \(OBO\)

Implement long-running operations that extend beyond a user's token lifetime by automatically refreshing tokens using the Microsoft Entra ID Auth SDK \(sidecar\). This guide shows you how to store user context, implement background processing, and handle token expiration.

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- **Microsoft Entra ID Auth SDK \(sidecar\)** deployed and running with refresh token support enabled. See [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation) for setup instructions.
- **Registered application in Microsoft Entra ID** - Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com). Refer to [Register an application](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp) for details. Record:

  - Application \(client\) ID
  - Directory \(tenant\) ID
  - Configure an **App ID URI** in the **Expose an API** section
  - Grant API permissions for downstream services \(e.g., Microsoft Graph permissions for tasks or reports your batch job accesses\)
  - Enable **Allow public client flows** if using device flow or similar patterns

- **Downstream APIs configured** in the SDK with appropriate scopes for long-running operations.
- **Storage mechanism** \(database, cache, or message queue\) to store user context during long-running background operations.
- **Appropriate permissions in Microsoft Entra ID** - Your account must have permissions to configure OBO flows and grant API permissions.

## Configuration

Configure longer refresh token lifetime in Microsoft Entra ID:

```bash
# Set refresh token lifetime (via Microsoft Graph PowerShell)
Connect-MgGraph -Scopes "Policy.Read.All", "Policy.ReadWrite.ApplicationConfiguration"

# Create token lifetime policy (example: 90 days)
$params = @{
    Definition = @(
        '{"TokenLifetimePolicy":{"Version":1,"AccessTokenLifetime":"1:00:00","RefreshTokenMaxInactiveTime":"90.00:00:00","RefreshTokenMaxAge":"90.00:00:00"}}'
    )
    DisplayName = "LongRunningOBOPolicy"
    IsOrganizationDefault = $false
}

New-MgPolicyTokenLifetimePolicy -BodyParameter $params
```

## Implementation pattern

Long-running OBO scenarios require three key components: storing user context when the operation starts, processing in the background, and handling token refresh automatically.

Note

The TypeScript and Python snippets in this section are illustrative pseudocode. Helper functions such as `ValidateToken`, `generateTaskId`, `storeUserContext`, `getUserContext`, `queueBackgroundTask`, `fetchData`, `generateReport`, `uploadToOneDrive`, `sendNotification`, `markTaskComplete`, `markTaskFailed`, `updateUserContext`, and `isTokenExpiredError` represent your application's own storage, queueing, and business logic. Replace them with the equivalent implementations from your stack.

### Store user context

Store the user's identity and tokens when initiating the operation:

```typescript
// When user initiates long-running task
interface UserContext {
  userId: string;
  userPrincipalName: string;
  originalToken: string;
  taskId: string;
  createdAt: Date;
}

async function initiateLongRunningTask(incomingToken: string): Promise<string> {
  // Extract user information from token
  const tokenClaims = ValidateToken(incomingToken);
  
  const taskId = generateTaskId();
  
  // Store user context
  const userContext: UserContext = {
    userId: tokenClaims.oid,
    userPrincipalName: tokenClaims.upn,
    originalToken: incomingToken,
    taskId: taskId,
    createdAt: new Date()
  };
  
  await storeUserContext(taskId, userContext);
  
  // Start background process
  await queueBackgroundTask(taskId);
  
  return taskId;
}
```

### Background processing

Process the queued task using the stored user context:

```typescript
async function processLongRunningTask(taskId: string) {
  // Retrieve user context
  const userContext = await getUserContext(taskId);
  
  // Use stored token with the SDK - refresh handled automatically
  try {
    // Step 1: Process data
    const data = await fetchData(userContext.originalToken);
    
    // Step 2: Generate report (may take hours)
    const report = await generateReport(data);
    
    // Step 3: Upload to user's OneDrive
    await uploadToOneDrive(userContext.originalToken, report);
    
    // Step 4: Send notification
    await sendNotification(userContext.originalToken, userContext.userId);
    
    await markTaskComplete(taskId);
  } catch (error) {
    // Handle token expiration
    if (isTokenExpiredError(error)) {
      await markTaskFailed(taskId, 'User token expired and could not be refreshed');
    } else {
      await markTaskFailed(taskId, error.message);
    }
  }
}

async function uploadToOneDrive(token: string, report: Buffer) {
  // SDK automatically handles token refresh
  const response = await fetch(
    `${sidecarUrl}/DownstreamApi/Graph?optionsOverride.RelativePath=me/drive/root:/reports/report.pdf:/content`,
    {
      method: 'PUT',
      headers: {
        'Authorization': token,
        'Content-Type': 'application/pdf'
      },
      body: report
    }
  );
  
  return await response.json();
}
```

### Periodic token refresh

Automatically refresh tokens before expiration:

```typescript
// Proactively refresh tokens before expiration
async function refreshTokenPeriodically(taskId: string) {
  const userContext = await getUserContext(taskId);
  
  // Call SDK to refresh token
  const response = await fetch(
    `${sidecarUrl}/AuthorizationHeader/Graph`,
    {
      headers: {
        'Authorization': userContext.originalToken
      }
    }
  );
  
  if (response.ok) {
    const data = await response.json();
    // Extract new token
    const newToken = data.authorizationHeader;
    
    // Update stored context
    userContext.originalToken = newToken;
    await updateUserContext(taskId, userContext);
  }
}
```

## Python example

The following example demonstrates a long-running task processor in Python using Flask or FastAPI:

```python
import asyncio
from datetime import datetime, timedelta
import requests
import os

class LongRunningTaskProcessor:
    def __init__(self, sidecar_url: str):
        self.sidecar_url = sidecar_url
    
    async def process_task(self, task_id: str, user_token: str):
        """Process a long-running task using the user's token."""
        try:
            # Step 1: Fetch data
            data = await self.fetch_data(user_token)
            
            # Step 2: Process (may take hours)
            await asyncio.sleep(3600)  # Simulate long processing
            result = await self.process_data(data)
            
            # Step 3: Upload result
            await self.upload_result(user_token, result)
            
            # Step 4: Notify user
            await self.notify_user(user_token, task_id)
            
        except Exception as e:
            print(f"Task {task_id} failed: {e}")
            # Handle failure
    
    async def fetch_data(self, token: str):
        """Fetch data from API - token refresh handled by the SDK."""
        response = requests.get(
            f"{self.sidecar_url}/DownstreamApi/Graph",
            params={'optionsOverride.RelativePath': 'me/messages'},
            headers={'Authorization': token}
        )
        response.raise_for_status()
        return response.json()
    
    async def upload_result(self, token: str, result):
        """Upload result to user's OneDrive."""
        response = requests.put(
            f"{self.sidecar_url}/DownstreamApi/Graph",
            params={'optionsOverride.RelativePath': 'me/drive/root:/results/output.json:/content'},
            headers={'Authorization': token},
            json=result
        )
        response.raise_for_status()
```

## Token expiration handling

When calling APIs through the SDK, implement retry logic to handle transient errors, including token expiration:

```typescript
async function callApiWithRetry(
  token: string,
  apiCall: (token: string) => Promise<any>,
  maxRetries: number = 3
): Promise<any> {
  for (let attempt = 1; attempt <= maxRetries; attempt++) {
    try {
      return await apiCall(token);
    } catch (error) {
      if (attempt < maxRetries) {
        // Wait and retry
        await new Promise(resolve => setTimeout(resolve, 1000 * attempt));
        continue;
      }
      throw error;
    }
  }
}
```

## Best practices and security

| Practice | Benefit |
| --- | --- |
| **Store minimal context** | Only persist essential user information needed to complete the operation |
| **Encrypt stored tokens** | Protect tokens at rest using encryption to prevent unauthorized access |
| **Secure key management** | Use secure key management practices for encryption keys |
| **Set context expiration** | Implement time limits on stored user contexts to avoid indefinite storage |
| **Access control** | Restrict access to stored user contexts to authorized processes only |
| **Handle refresh failures** | Detect when refresh tokens expire and notify users appropriately |
| **Monitor token usage** | Track refresh token consumption to understand token lifetime and usage patterns |
| **Audit logging** | Log all token usage and long-running operations for compliance and troubleshooting |
| **User consent** | Obtain and document user consent for long-running operations before beginning |
| **Revocation support** | Allow users to cancel long-running operations and revoke token access |
| **Notify users** | Keep users informed of long-running task status, especially if operations fail |
| **Implement cleanup** | Remove completed task contexts from storage to prevent accumulation |

## Limitations

- **Refresh token lifetime**: Refresh tokens have a maximum lifetime \(typically 90 days\), limiting how long operations can run
- **User consent revocation**: Users can revoke consent at any time, causing operations to fail
- **Conditional access changes**: Administrators may change conditional access policies during processing
- **MFA interruptions**: Multi-factor authentication requirements may prevent token refresh
- **Session termination**: User sessions may be terminated by administrators or security policies

## Related content

- [Agent autonomous batch processing](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/agent-autonomous-batch)
- [Using managed identity](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/managed-identity)
- [Security](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)
- [Call a downstream API](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/call-downstream-api)
