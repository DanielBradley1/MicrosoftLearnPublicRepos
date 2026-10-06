<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/adding-ai-services -->
<!-- Sitemap-Last-Modified: 2026-10-01 -->

# Add AI services and orchestration

The Microsoft 365 Agents SDK creates an agent that provides a container for developers to add their chosen AI Services. The agent can:

- Manage state across turns, including AI chat history.
- Store state or data persistently in the storage of your choice \(with built-in options for `Blobs` and `CosmosDb`\)
- Manage activities and events

The agent can be deployed in any channel, including Microsoft Copilot and Microsoft Teams.

AI services typically contain chat endpoints, but can also include assistants or hosted agents, such as agents built in Copilot Studio. Orchestration can be added based on the business logic and how developers want to manage state and invoke tools/plugins. Developers can choose to implement multi-agent scenarios and patterns depending on their requirements, different tech platforms as required based on their defined business logic.

## Add Semantic Kernel and Azure OpenAI

You have the choice where you want to add AI services to the agent.

You can choose to implement AI services at the same time the core agent container gets built, together with the services in a web application.

- [.Net](#tabpanel_1_dotnet)
- [JavaScript](#tabpanel_1_nodejs)
- [Python](#tabpanel_1_python)

You can see this behavior in the [Semantic Kernel multi-turn with weather agent .NET sample](https://github.com/microsoft/Agents/tree/main/samples/dotnet/semantic-kernel-multiturn) on the GitHub samples repo.

```csharp
builder.Services.AddKernel();

builder.Services.AddAzureOpenAIChatCompletion(
    deploymentName: builder.Configuration.GetSection("AIServices:AzureOpenAI").GetValue<string>("DeploymentName"),
    endpoint: builder.Configuration.GetSection("AIServices:AzureOpenAI").GetValue<string>("Endpoint"),
    apiKey: builder.Configuration.GetSection("AIServices:AzureOpenAI").GetValue<string>("ApiKey"),
    modelId: builder.Configuration.GetSection("AIServices:OpenAI").GetValue<string>("ModelId")
);
```

For JavaScript, see the [LangChain multi-turn with weather agent JavaScript sample](https://github.com/microsoft/Agents/tree/main/samples/nodejs/langchain-multiturn) on the GitHub samples repo.

For Python, see the [Semantic Kernel multi-turn with weather agent Python sample](https://github.com/microsoft/Agents/tree/main/samples/python/semantic-kernel-multiturn) on the GitHub samples repo.

Developers can create different agents using these services, each with their own plugin. You can then pass in the agents as parameters to the Agents SDK container.

You can also choose to implement AI services elsewhere. For example, you can implement the services in the agent class that gets built and passed to the agent at runtime. This class appears as `MyAgent` in some of the samples. This approach allows you to use Semantic Kernel or even multiple orchestrators, and is built separately from the main agent.

- [.Net](#tabpanel_2_dotnet)
- [JavaScript](#tabpanel_2_nodejs)
- [Python](#tabpanel_2_python)

```csharp
var builder = Kernel.CreateBuilder();

builder.AddAzureOpenAIChatCompletion(
    deploymentName: deploymentName,
    endpoint: endpoint,
    apiKey: apiKey);

var kernel = builder.Build();
```

For JavaScript, see the [LangChain multi-turn with weather agent JavaScript sample](https://github.com/microsoft/Agents/tree/main/samples/nodejs/langchain-multiturn) on the GitHub samples repo.

For Python, see the [Semantic Kernel multi-turn with weather agent Python sample](https://github.com/microsoft/Agents/tree/main/samples/python/semantic-kernel-multiturn) on the GitHub samples repo.
