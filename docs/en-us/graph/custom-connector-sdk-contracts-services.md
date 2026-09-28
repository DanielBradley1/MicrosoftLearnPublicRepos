<!-- Source: https://learn.microsoft.com/en-us/graph/custom-connector-sdk-contracts-services -->
<!-- Sitemap-Last-Modified: 2025-05-21 -->

# Copilot connectors SDK services

This article describes the services that are part of the contract protocol buffer files. Implement these services as part of the connector.

| Services | Description |
| :--- | :--- |
| [ConnectorInfo](https://learn.microsoft.com/en-us/graph/custom-connector-sdk-contracts-connectorinfo) | Includes APIs to get information about the connector. If you're using the Visual Studio extension, you can use the default implementation for this service without changes. |
| [ConnectionManagement](https://learn.microsoft.com/en-us/graph/custom-connector-sdk-contracts-connectionmanagement) | Contains APIs that are called during the process of **custom connector connection creation** in the Microsoft 365 admin center. |
| [ConnectorCrawl](https://learn.microsoft.com/en-us/graph/custom-connector-sdk-contracts-connectorcrawler) | Includes APIs that are called during a crawl. |
| [ConnectorOAuth](https://learn.microsoft.com/en-us/graph/custom-connector-sdk-contracts-connectoroauth) | Service for OAuth flows such as refreshing access tokens during crawls. |

You can download the contract protocol buffer files from the Copilot connectors SDK [contracts](https://github.com/microsoftgraph/msgraph-connectors-sdk/tree/main/Contracts) page on GitHub.
