<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/using-semantic-kernel-agent-framework -->
<!-- Sitemap-Last-Modified: 2025-10-21 -->

# Use Semantic Kernel and Agent Framework in Agents SDK

The Microsoft 365 Agents SDK focuses on supporting the conversation management, channel/client management, and authentication functionality, within an agent. The Agents SDK uses *Activity Protocol* as the communication protocol between client and code. By providing turn context management, the code accepts an `Activity` and gives the opportunity for the developer to add custom business logic based on the information provided from the client, found inside an `Activity`. From there, developers can create new activities to be sent back.

The Agents SDK allows developers to create agents and choose any AI model, services and orchestrators so they can select what meets their needs, while giving them flexibility to change those components when required. This includes supporting single agent, and multi-agent to agent workflows.

Agent Framework currently supports C# and Python in public preview status. The code snippets in this article use C#. However, the syntax is similar across other supported languages.

## Add orchestration and AI

Lets first review the structure of an agent using the Microsoft 365 Agents SDK.

### Program.cs

`Program.cs` manages the hosting component of the agent, utilizing the hosting infrastructure of your choice, typically based on the language you're building your agent in. For example, in C#/.NET, it uses the ASP.NET hosting infrastructure to build an application. As that application is being built, components or services are added, such as:

- `CloudAdapter`: The main channel adapter that is used by your code to interact with the client, accepts HTTP requests and creates the `TurnContext` object.
- `IStorage` interface: Registers the storage you want to use. Many samples use `Memory Storage` that should be switched out to more persisted storage like `Blob` or `CosmosDb` for production use. Custom storage providers are supported.
- `AgentApplicationOptions`: Is used with `AgentApplication` and loads options from the config in your code such as hosting details, logging, and extensions \(for example, the Microsoft Teams Extension\)
- `AddAgent<youragent>`: Your code includes an agent implementing the `AgentApplication` class from the SDK that contains your main agentic business logic, for example, `EchoBot.cs`. This loads the agent.
- Routing logic: Adds a route \(api/messages\) to your host and register an endpoint

### Orchestration options

The Agents SDK allows developers to use any orchestration SDK in their code, which typically interfaces with the chosen AI service provider\(s\). A common orchestration option is the Semantic Kernel SDK. You can find an example of a Semantic Kernel sample using the Microsoft 365 Agents SDK can be found in the [Semantic Kernel multi-turn sample](https://github.com/microsoft/Agents/tree/main/samples/dotnet/semantic-kernel-multiturn).

#### Orchestrate with Semantic Kernel

Semantic Kernel uses the `Kernel` object together with the `AzureOpenAIChatCompletion` object to orchestrate requests to the configured Azure OpenAI or Foundry endpoints/deployments. The `Kernel` object references the AI services you set up in `Program.cs`, manages and publishes plugins, and provides execution context to a function or planner. Methods from Semantic Kernel run from the `Kernel` object.

By registering your `Kernel` object in the builder object inside of `Program.cs`, you can configure your single `Kernel` object to manage these activities and avoid reinstantiating it every time \(along with plugins etc.\). You can register it in a few ways, the easiest is by using the built-in helper method that creates the kernel object and registers it as a singleton:

```csharp
builder.Services.AddKernel()
```

In the following example, the `Kernel` is then referenced in your `EchoBot.cs` class and uses dependency injection to look up the registration, so that it requesting to reuse the same object created at registration time.

```csharp
private readonly IKernal _kernel
```

This object gets populated from your registration and used in the creation of the `EchoBot` object, that takes `AgentApplicationOptions` and the `kernel` at time of creation. The `EchoAgent` class includes event listeners. For example, `OnActivity` waits for specific actions from the client, and when they occur, points to your custom methods that have your business logic. That business logic can use the `Kernel` object you have available from the creation of your class.

#### Orchestrate with Semantic Kernel using TurnContext and TurnState

Semantic Kernel provides the `Kernel` object that acts as the runner to 'orchestrate' with the model, register and use plugins, and invoke a planner. Additionally it can track history using `ChatHistory` and it's up the developer on how they want to blend these objects to achieve the agent and user experience they require. For example, creating a `ChatHistory` record and passing the `turnState` information into it, allows the `Kernel` to be aware of the information from the Channel, which is stored in turnState using the Agents SDK so it can be used in the `Kernel` during orchestration time.

```csharp
ChatHistory chatHistory = turnState.Conversation.GetValue("conversation.chatHistory", () => new ChatHistory());
```

There are multiple patterns you can use to integrate and use Semantic Kernel with the Agents SDK. It can be seen a good practice to abstract the creation of the Semantic Kernel 'agent' into its own class \(separate from the main Agent, typically `EchoAgent` in samples, that manages the `TurnContext`\) and instead, invoke the Semantic Kernel agent when required, passing in the `kernel` object made from when `EchoAgent.cs` gets created each turn.

The kernel object uses an `Agent` that has instructions, settings, and plugins registered against it. These plugins/tools are typically their own class.

You can register or import plugins with Semantic Kernel from the `Kernel` object. The plugin logic is typically held in their own class with methods. Those classes are decorated with `[KernelFunction, Description("Get the current date")]` to provide more instructions to the language model on what this tool can be used for.

```csharp
this._agent.Kernel.Plugins.Add(KernelPluginFactory.CreateFromType<DateTimePlugin>(serviceProvider: service));
```

The next section will cover what is changed between Semantic Kernel and the Microsoft Agent Framework.

#### Orchestrate with Agent Framework

Microsoft Agent Framework is an open-source development kit that comes out of a progression of multiple SDKs in Microsoft. Most notably, Agent Framework combines the Semantic Kernel and AutoGen orchestrators into one single orchestrator that developers can use in their agent to provide orchestration for Agents. More information on Agent Framework can be found here [Agent Framework Semantic Kernel migration](https://github.com/microsoft/agent-framework/tree/main/dotnet/samples/SemanticKernelMigration).

This section covers how the Agent Framework can be used in place of Semantic Kernel within the Microsoft 365 Agents SDK. It is recommended to review the Semantic Kernel section above for context.

Just like Semantic Kernel, you can use Agent Framework as the orchestrator for your agent using Microsoft 365 Agents SDK. There are some notable differences, the main one being there's no longer a `Kernel` object to use.

What is used instead is in the `Program.cs` class - the `IChatClient` that is created as a singleton, wrapped by the `ChatClientAgent` object and uses with the `AzureOpenAIClient` to make LLM calls to supported providers. This approach can be seen as the closest thing as a replacement to the Kernel object from Semantic Kernel.

```csharp
builder.Services.AddSingleton<IChatClient>(sp => { return new AzureOpenAIClient(endpointUri, apiKeyCredential).GetChatClient(deployment).AsIChatClient(); });
```

The `EchoBot.cs` class still acts as the main agent that receives an `Activity` from the client using the Agents SDK. This class uses mostly, the same structure as with Semantic Kernel, however instead of requiring the `IKernel` type object that Semantic Kernel used, the class now requires the `IChatClient` object. In the sample, `EchoBot.cs` also uses dependency injection to build the `IChatClient`, registers it as a Singleton, and reuses that object every time the `EchoBot` class is created each turn. \(Where IChatClient is wrapped by `ChatClientAgent` in `EchoAgent.cs`.\)

```csharp
private readonly ChatClientAgent AFClient;
public EchoBot(AgentApplicationOptions options, IChatClient chatClient) : base(options)
{
 // 
}
```

These cover some small changes in the creation of the agent. There are also updates to how tools are registered \(previously referred to as plugins in Semantic Kernel\) and threads are created/used. The same abstractions to separate classes can apply. For example, when you create the `ChatClientAgent` it includes options such as temperature, instructions, and tool registration, and is wrapped by a `IChatAgent` that was made as a singleton using dependency injection. This action can be in a separate class or included in `EchoBot.cs` as in the sample.

```csharp
var toolOptions = new ChatOptions
{
    Temperature = (float?)0.2,
    Tools = new List<AITool>()
};
toolOptions.Tools.Add(AIFunctionFactory.Create(DateTimeFunctionTool.getDate));

AFClient = new ChatClientAgent(chatClient, new ChatClientAgentOptions { Name = "Helper", Instructions = """ Act like a Cat""", ChatOptions = toolOptions });
```

Next, using the Agents SDK, create your event listeners in your `EchoBot.cs` and create your custom methods that include your business logic, using methods available in the new Agent Framework object you created of type `ChatClientAgent` to manage the orchestration behavior, such as `RunAsync`:

```csharp
protected async Task OnMessageAsync(ITurnContext turnContext, ITurnState turnState, CancellationToken cancellationToken)
    {
        var userText = turnContext.Activity.Text?.Trim() ?? string.Empty;
        var conversationId = turnContext.Activity.Conversation.Id;
        var thread = _threads.GetOrAdd(conversationId, _ => AFClient.GetNewThread());
        var result = await AFClient.RunAsync(userText, thread, cancellationToken: cancellationToken);

        await turnContext.SendActivityAsync(result.Text, cancellationToken: cancellationToken);
    }
```

Tools in Agent Framework should be their own class and decorated with descriptors. For example, `[Description("Use the tool to be able to return back the date and time right now)")]`

## Summary

This article covers the structure of an agent built using the Microsoft 365 Agents SDK. The article explains how to add Semantic Kernel as the orchestrator with AI Foundry or Azure OpenAI endpoints. It also covers the main differences between using Semantic Kernel versus Microsoft Agent Framework orchestration.

## Next steps

- [Review the list of prebuilt events you can respond to from the client](https://github.com/microsoft/Agents-for-net/blob/main/src/libraries/Builder/Microsoft.Agents.Builder/App/AgentApplication.cs)
- [Review the list of prebuilt events you can sent back to the client](https://github.com/microsoft/Agents-for-net/blob/main/src/libraries/Builder/Microsoft.Agents.Builder/TurnContext.cs)
- [Provisioning an Azure Bot to use with Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-azure-bot-service-manually)
- [Configure your Agent for OAuth](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-oauth-configuration-dotnet)
