<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/agent-autonomous-batch -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Scenario: Agent autonomous batch processing

Implement autonomous batch processing using agent identities to perform operations without user context. This scenario enables batch processing of large data volumes, scheduled tasks via cron jobs, background operations outside user sessions, and secure service-to-system workflows. This guide shows you how to configure the Microsoft Entra ID Auth SDK \(sidecar\) and implement common patterns like scheduled jobs and queue-based processing.

## Prerequisites

- An Azure account with an active subscription. [Create an account for free](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- **Microsoft Entra ID Auth SDK \(sidecar\)** deployed in your environment with agent identity support enabled. See [Installation Guide](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation) for setup instructions.
- **Registered application in Microsoft Entra ID** - Register a new app in the [Microsoft Entra admin center](https://entra.microsoft.com) for your batch service. Refer to [Register an application](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp) for details. Record:

  - Application \(client\) ID
  - Directory \(tenant\) ID
  - Create a client secret or certificate for authentication
  - Configure application permissions for the downstream APIs your batch job will access \(e.g., Microsoft Graph permissions\)

- **Appropriate permissions in Microsoft Entra ID** - Your account must have permissions to register applications, configure agent identities, and grant application permissions.
- **Access to downstream APIs** - Target APIs \(such as Microsoft Graph\) must be accessible and configured with the required scopes for your batch operations.

## Agent identity setup

For details on creating agent identities and configuring federated identity credentials, see the [Microsoft agent identity platform documentation](https://learn.microsoft.com/en-us/entra/agent-id/identity-platform).

### Key configuration requirements

When setting up an agent identity for batch processing:

1. **Federated Identity Credentials**: Configure workload identity federation to allow your application to obtain tokens without storing secrets
2. **Application Permissions**: Grant the agent identity only the Microsoft Graph API permissions \(or other downstream API permissions\) that the batch operation requires
3. **Environment Variables**: Set `ENTRA_SDK_URL` to point to your running Microsoft Entra ID Auth SDK \(sidecar\) instance, and store the agent `CLIENT_ID` for use in your batch processing code
4. **Token Scope**: Ensure the Microsoft Entra ID Auth SDK \(sidecar\) is configured to request tokens in the service principal's context, not on behalf of a user

## Implementation

The following code snippets demonstrate how to implement autonomous batch processing with agent identities. The key principle is to pass the agent identity to the Microsoft Entra ID Auth SDK \(sidecar\) and request an application token instead of a user-delegated token.

### TypeScript

Request an application token using the agent identity to process batch operations:

```typescript
async function processBatchWithAgent(
  incomingToken: string,
  agentIdentity: string
) {
  const sdkUrl = process.env.ENTRA_SDK_URL!;
  
  // Get users list using agent identity (autonomous)
  const response = await fetch(
    `${sdkUrl}/DownstreamApi/Graph?` +
    `AgentIdentity=${agentIdentity}&` +
    `optionsOverride.RelativePath=users&` +
    `optionsOverride.RequestAppToken=true`,
    {
      headers: {
        'Authorization': incomingToken
      }
    }
  );
  
  const result = await response.json();
  const users = JSON.parse(result.content);
  
  // Process each user
  for (const user of users.value) {
    await processUser(user);
  }
}

async function scheduledReportGeneration() {
  const agentIdentity = process.env.AGENT_CLIENT_ID!;
  const token = await getSystemToken();
  
  // Generate reports for all departments
  const departments = await getDepartments(token, agentIdentity);
  
  for (const dept of departments) {
    await generateDepartmentReport(token, agentIdentity, dept);
  }
}
```

### Python

Here's the equivalent implementation in Python using the requests library:

```python
import requests
import os
import json

def process_batch_with_agent(incoming_token: str, agent_identity: str):
    """Process batch using autonomous agent."""
    sdk_url = os.getenv('ENTRA_SDK_URL', 'http://localhost:5000')
    
    # Get users using agent identity
    response = requests.get(
        f"{sdk_url}/DownstreamApi/Graph",
        params={
            'AgentIdentity': agent_identity,
            'optionsOverride.RelativePath': 'users',
            'optionsOverride.RequestAppToken': 'true'
        },
        headers={'Authorization': incoming_token}
    )
    
    result = response.json()
    users = json.loads(result['content'])
    
    # Process each user
    for user in users['value']:
        process_user(user)
```

## Batch processing patterns

Different scenarios call for different batch processing approaches. The following code snippets provide patterns for the most common implementations that leverage agent identities.

### Scheduled job

Use scheduled jobs when you need to run batch operations at specific times:

```typescript
// Cron-based batch processor
import cron from 'node-cron';

// Run every day at 2 AM
cron.schedule('0 2 * * *', async () => {
  console.log('Starting nightly batch process');
  
  try {
    await runAutonomousBatch(
      process.env.AGENT_CLIENT_ID!
    );
    console.log('Batch completed successfully');
  } catch (error) {
    console.error('Batch failed:', error);
  }
});
```

### Queue-based processing

Use queue-based processing when batch items arrive asynchronously or unpredictably:

```typescript
// Process messages from queue
async function processQueueMessages(queueClient, agentIdentity: string) {
  while (true) {
    const messages = await queueClient.receiveMessages(10);
    
    for (const message of messages) {
      try {
        await processMessage(message, agentIdentity);
        await queueClient.deleteMessage(message);
      } catch (error) {
        console.error('Message processing failed:', error);
      }
    }
    
    await sleep(5000);
  }
}
```

## Best practices

1. **Use application permissions**: Grant only the application permissions required for the batch operation, following the principle of least privilege
2. **Implement retry logic**: Handle transient failures with exponential backoff to improve reliability
3. **Monitor progress**: Track batch job progress and log key metrics to enable troubleshooting and performance analysis
4. **Limit scope**: Request only the necessary permissions for each operation
5. **Audit operations**: Log all agent actions with details about what was processed and by which agent
6. **Handle throttling**: Respect API rate limits and implement appropriate backoff strategies

## Related content

- [Agent identities](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/agent-identities)
- [Security](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)
- [Call a downstream API](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/call-downstream-api)
- [Configuration](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
