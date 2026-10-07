<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/connector-agent-frequently-asked-questions -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Microsoft Graph connector agent FAQ

To use on-premises Microsoft 365 Copilot connectors, you must install the Microsoft Graph connector agent. The connector agent allows for secure data transfer between on-premises data and the Copilot connector APIs.

This article provides answers to frequently asked questions related to the Microsoft Graph connector agent.

## How does the Microsoft Graph connector agent interact with its system, and where is the indexed data stored?

The agent is installed on-premises and needs access to the data source. When the account is authorized, the agent crawls the data and communicates with the Microsoft 365 Copilot connector services to push data to the index. The data indexed through Microsoft 365 Copilot connectors is in the same location.

## Where should the Microsoft Graph connector agent be installed?

Install the agent on a computer on the same network as the data source. It doesn't have to be installed on the same computer that hosts the data source. The data source URL must be accessible to the Microsoft Graph Connector Agent.

## Why does the Microsoft Graph connector agent require the ExternalConnection.ReadWrite.OwnedBy permission?

The `ExternalConnection.ReadWrite.OwnedBy` permission allows the agent to read and write external connection settings on behalf of the admin, but it can't access or modify anything beyond its granted permissions.

## Can the Microsoft Graph connector agent be installed on multiple servers, and does the service run on both?

You can install the Microsoft Graph Connector Agent on multiple computers, for multiple connections. One agent can handle multiple connections. The crawl performance depends on the number of connections used, crawl frequency, and number of items. We recommend using no more than three connections per agent.

## What happens if the Microsoft Graph connector agent is interrupted during a crawl?

The Microsoft Graph connector agent is designed to handle interruptions automatically in most cases:

- It automatically retries temporary issues, such as brief network interruptions or timeouts.
- It saves crawl progress and resumes from the last saved point after a restart or brief outage instead of starting over.
- If the agent remains offline longer than the connection's refresh or sync interval, the in-progress crawl might not resume. Instead, a new crawl starts during the next scheduled run.

This behavior helps prevent duplicate processing while keeping indexed content up to date with minimal administrator intervention. If the issue persists, check the connection status and crawl history in the Microsoft 365 admin center.

## How do I configure the Microsoft Graph connector agent for GCC, GCC High, or DoD?

For Government Cloud deployments, configure Authority.CloudInstanceUrl, Scopes, and GcsBaseUrl using values from the same environment. Refer to the Government cloud configuration note of the Microsoft Graph connector agent documentation for the latest values.

## Related content

- [Microsoft 365 Copilot connectors FAQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/frequently-asked-questions)
- [Connectors overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/overview)
- [Connectors gallery](https://learn.microsoft.com/en-us/microsoft-365/copilot/connectors/connectors-gallery)
