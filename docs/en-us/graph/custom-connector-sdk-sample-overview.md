<!-- Source: https://learn.microsoft.com/en-us/graph/custom-connector-sdk-sample-overview -->
<!-- Sitemap-Last-Modified: 2025-05-21 -->

# Build your first custom Copilot connector

Microsoft 365 Copilot connectors \(formerly Microsoft Graph connectors\) enable you to add your own data into Microsoft Graph and have it power various Microsoft 365 experiences. The following set of articles show you how to use the [Copilot connectors SDK](https://learn.microsoft.com/en-us/graph/custom-connector-sdk-overview) to create a custom connector in C# and use it to power Microsoft Search. This custom connector uses a sample data appliance parts inventory in a CSV file for the Contoso Appliance Repair organization.

Note

If you want to use a language other than C# to build your connector, see [Build a connector using other languages](https://learn.microsoft.com/en-us/graph/custom-connector-sdk-other-languages).

## How does the custom connector work?

The sample code included in the [Develop your connector](https://learn.microsoft.com/en-us/graph/custom-connector-sdk-sample-create) section creates a gRPC server that runs the custom connector on your virtual machine. Your custom connector code is responsible for fetching the data from the data source which must be accessible from your virtual machine. A gRPC client from the [Microsoft Graph connector agent](https://learn.microsoft.com/en-us/microsoftsearch/graph-connector-agent) running on the same computer makes requests over gRPC to the server to fetch the required response. The Microsoft Graph connector agent integrates the custom connector with the Microsoft 365 admin center, ingests the content into Microsoft Graph and performs other platform tasks through the orchestration framework. For details on the platform tasks, see [connector agent capabilities](https://learn.microsoft.com/en-us/graph/custom-connector-sdk-overview#microsoft-graph-connector-agent-capabilities).

![A diagram of the architecture of an SDK-based connector](https://learn.microsoft.com/en-us/graph/images/connectors-sdk/architecture.png)

## Next step

[Develop your connector](https://learn.microsoft.com/en-us/graph/custom-connector-sdk-sample-create)
