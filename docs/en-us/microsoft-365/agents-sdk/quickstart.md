<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/quickstart -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Quickstart: Create and test a basic agent

This quickstart guides you through creating a [custom engine agent](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent) that replies back with whatever message you send to it.

## Prerequisites

- Python 3.9 or newer.

  - To install Python, go to [https://www.python.org/downloads/](https://www.python.org/downloads/), and follow the instructions for your operating system.
  - To verify the version, in a terminal window type `python --version`.

- A code editor of your choice. These instructions use [Visual Studio Code](https://code.visualstudio.com/download).

  If you use Visual Studio Code, install the [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

## Initialize the project and install the SDK

Create a Python project and install the required dependencies.

1. Open a terminal and create a new folder

   ```cmd
   mkdir echo
   cd echo
   ```

2. Open the folder using Visual Studio Code using this command:

   ```cmd
   code .
   ```

3. Create a virtual environment with the method of your choice and activate it either through Visual Studio Code or in a terminal.

   When using Visual Studio Code, you can use these steps with the [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python) installed.

   1. Press F1, type `Python: Create environment`, and press Enter.

      1. Select **Venv** to create a `.venv` virtual environment in the current workspace.
      2. Select a Python installation to create the virtual environment.

         The value might look like this:

         `Python 1.13.6 ~\AppData\Local\Programs\Python\Python313\python.exe`

4. Install the Agents SDK

   Use [pip](https://pip.pypa.io/) to install the [microsoft-agents-hosting-aiohttp](https://pypi.org/project/microsoft-agents-hosting-aiohttp/) package with this command:

   ```cmd
   pip install microsoft-agents-hosting-aiohttp
   ```

## Create the server application and import the required libraries

1. Create a file named `start_server.py`, copy the following code, and paste it in:

   ```python
   # start_server.py
   from os import environ
   from microsoft_agents.hosting.core import AgentApplication, AgentAuthConfiguration
   from microsoft_agents.hosting.aiohttp import (
      start_agent_process,
      jwt_authorization_middleware,
      CloudAdapter,
   )
   from aiohttp.web import Request, Response, Application, run_app


   def start_server(
      agent_application: AgentApplication, auth_configuration: AgentAuthConfiguration
   ):
      async def entry_point(req: Request) -> Response:
         agent: AgentApplication = req.app["agent_app"]
         adapter: CloudAdapter = req.app["adapter"]
         return await start_agent_process(
               req,
               agent,
               adapter,
         )

      APP = Application(middlewares=[jwt_authorization_middleware])
      APP.router.add_post("/api/messages", entry_point)
      APP.router.add_get("/api/messages", lambda _: Response(status=200))
      APP["agent_configuration"] = auth_configuration
      APP["agent_app"] = agent_application
      APP["adapter"] = agent_application.adapter

      try:
         run_app(APP, host="localhost", port=environ.get("PORT", 3978))
      except Exception as error:
         raise error
   ```


   This code defines a `start_server` function we'll use in the next file.

2. In the same directory, create a file named `app.py` with the following code.

   ```python
   # app.py
   from microsoft_agents.hosting.core import (
      AgentApplication,
      TurnState,
      TurnContext,
      MemoryStorage,
   )
   from microsoft_agents.hosting.aiohttp import CloudAdapter
   from start_server import start_server
   ```

## Create an instance of the agent as an AgentApplication

In `app.py`, add the following code to create the `AGENT_APP` as an instance of the `AgentApplication`, and implement three routes to respond to three events:

- Conversation Update
- the message `/help`
- any other activity

```python
AGENT_APP = AgentApplication[TurnState](
    storage=MemoryStorage(), adapter=CloudAdapter()
)

async def _help(context: TurnContext, _: TurnState):
    await context.send_activity(
        "Welcome to the Echo Agent sample 🚀. "
        "Type /help for help or send a message to see the echo feature in action."
    )

AGENT_APP.conversation_update("membersAdded")(_help)

AGENT_APP.message("/help")(_help)


@AGENT_APP.activity("message")
async def on_message(context: TurnContext, _):
    await context.send_activity(f"you said: {context.activity.text}")
```

## Start the web server to listen in localhost:3978

At the end of `app.py`, start the web server using `start_server`.

```python
if __name__ == "__main__":
    try:
        start_server(AGENT_APP, None)
    except Exception as error:
        raise error
```

## Run the agent locally in anonymous mode

From your terminal, run this command:

```cmd
python app.py
```

The terminal should return the following:

```cmd
======== Running on http://localhost:3978 ========
(Press CTRL+C to quit)
```

## Test the agent locally

1. From another terminal \(to keep the agent running\) install the [Microsoft 365 Agents Playground](https://www.npmjs.com/package/@microsoft/teams-app-test-tool) with this command:

   ```cmd
   npm install -g @microsoft/teams-app-test-tool
   ```


   Note


   This command uses npm because the Microsoft 365 Agents Playground isn't available using [pip](https://pip.pypa.io/).


   The terminal should return something like:


   ```cmd
   added 1 package, and audited 130 packages in 1s

   19 packages are looking for funding
   run `npm fund` for details

   found 0 vulnerabilities
   ```

2. Run the test tool to interact with your agent using this command:

   ```cmd
   teamsapptester
   ```


   The terminal should return something like:


   ```cmd
   Telemetry: agents-playground-cli/serverStart {"cleanProperties":{"options":"{\"configFileOptions\":{\"path\":\"<REDACTED: user-file-path>\"},\"appConfig\":{},\"port\":56150,\"disableTelemetry\":false}"}}

   Telemetry: agents-playground-cli/cliStart {"cleanProperties":{"isExec":"false","argv":"<REDACTED: user-file-path>,<REDACTED: user-file-path>"}}

   Listening on 56150
   Microsoft 365 Agents Playground is being launched for you to debug the app: http://localhost:56150
   started web socket client
   started web socket client
   Waiting for connection of endpoint: http://127.0.0.1:3978/api/messages
   waiting for 1 resources: http://127.0.0.1:3978/api/messages
   wait-on(37568) complete
   Telemetry: agents-playground-server/getConfig {"cleanProperties":{"internalConfig":"{\"locale\":\"en-US\",\"localTimezone\":\"America/Los_Angeles\",\"channelId\":\"msteams\"}"}}

   Telemetry: agents-playground-server/sendActivity {"cleanProperties":{"activityType":"installationUpdate","conversationId":"5305bb42-59c9-4a4c-a2b6-e7a8f4162ede","headers":"{\"x-ms-agents-playground\":\"true\"}"}}

   Telemetry: agents-playground-server/sendActivity {"cleanProperties":{"activityType":"conversationUpdate","conversationId":"5305bb42-59c9-4a4c-a2b6-e7a8f4162ede","headers":"{\"x-ms-agents-playground\":\"true\"}"}}
   ```

The `teamsapptester` command opens your default browser and connects to your agent.

![Your agent in the agents playground](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/quickstart-nodejs/microsoft-365-agents-playground.png)

Now you can send any message to see the echo reply, or send the message `/help` to see how that message is routed to the `_help` handler.

This quickstart guides you through creating a [custom engine agent](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent) that replies back with whatever message you send to it.

## Prerequisites

- Node.js v22 or newer

  - To install Node.js go to [nodejs.org](https://nodejs.org/), and follow the instructions for your operating system.
  - To verify the version, in a terminal window type `node --version`.

- A code editor of your choice. These instructions use [Visual Studio Code](https://code.visualstudio.com/download).

## Initialize the project and install the SDK

Use `npm` to initialize a node.js project by creating a package.json and installing the required dependencies

1. Open a terminal and create a new folder

   ```cmd
   mkdir echo
   cd echo
   ```

2. Initialize the node.js project

   ```cmd
   npm init -y
   ```

3. Install the Agents SDK

   ```cmd
   npm install @microsoft/agents-hosting-express
   ```

4. Open the folder using Visual Studio Code using the this command:

   ```cmd
   code .
   ```

## Import the required libraries

Create the file `index.mjs` and import the following NPM packages into your application code:

- [@microsoft/agents-hosting](https://learn.microsoft.com/en-us/javascript/api/%40microsoft/agents-hosting/?view=agents-sdk-js-latest&preserve-view=true)
- [@microsoft/agents-hosting-express](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting-express/?view=agents-sdk-js-latest&preserve-view=true)

```javascript
// index.mjs
import { startServer } from '@microsoft/agents-hosting-express'
import { AgentApplication, MemoryStorage } from '@microsoft/agents-hosting'
```

## Implement the EchoAgent as an AgentApplication

In `index.mjs`, add the following code to create the `EchoAgent` extending the [AgentApplication](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/agentapplication), and implement three routes to respond to three events:

- Conversation Update
- the message `/help`
- any other activity

```javascript
class EchoAgent extends AgentApplication {
  constructor (storage) {
    super({ storage })

    this.onConversationUpdate('membersAdded', this._help)
    this.onMessage('/help', this._help)
    this.onActivity('message', this._echo)
  }

  _help = async context => 
    await context.sendActivity(`Welcome to the Echo Agent sample 🚀. 
      Type /help for help or send a message to see the echo feature in action.`)

  _echo = async (context, state) => {
    let counter= state.getValue('conversation.counter') || 0
    await context.sendActivity(`[${counter++}]You said: ${context.activity.text}`)
    state.setValue('conversation.counter', counter)
  }
}
```

## Start the web server to listen in localhost:3978

At the end of `index.mjs` start the web server using [startServer](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting-express/?view=agents-sdk-js-latest&preserve-view=true#@microsoft-agents-hosting-express-startserver) based on express using [MemoryStorage](https://learn.microsoft.com/en-us/javascript/api/@microsoft/agents-hosting/memorystorage?view=agents-sdk-js-latest&preserve-view=true) as the turn state storage.

```javascript
startServer(new EchoAgent(new MemoryStorage()))
```

## Run the agent locally in anonymous mode

From your terminal, run this command:

```cmd
node index.mjs
```

The terminal should return this:

```cmd
Server listening to port 3978 on sdk 0.6.18 for appId undefined debug undefined
```

## Test the agent locally

1. From another terminal \(to keep the agent running\) install the [Microsoft 365 Agents Playground](https://www.npmjs.com/package/@microsoft/teams-app-test-tool) with this command:

   ```cmd
   npm install -D @microsoft/teams-app-test-tool
   ```


   The terminal should return something like:


   ```cmd
   added 1 package, and audited 130 packages in 1s

   19 packages are looking for funding
   run `npm fund` for details

   found 0 vulnerabilities
   ```

2. Run the test tool to interact with your agent using this command:

   ```cmd
   node_modules/.bin/teamsapptester
   ```


   The terminal should return something like:


   ```cmd
   Telemetry: agents-playground-cli/serverStart {"cleanProperties":{"options":"{\"configFileOptions\":{\"path\":\"<REDACTED: user-file-path>\"},\"appConfig\":{},\"port\":56150,\"disableTelemetry\":false}"}}

   Telemetry: agents-playground-cli/cliStart {"cleanProperties":{"isExec":"false","argv":"<REDACTED: user-file-path>,<REDACTED: user-file-path>"}}

   Listening on 56150
   Microsoft 365 Agents Playground is being launched for you to debug the app: http://localhost:56150
   started web socket client
   started web socket client
   Waiting for connection of endpoint: http://127.0.0.1:3978/api/messages
   waiting for 1 resources: http://127.0.0.1:3978/api/messages
   wait-on(37568) complete
   Telemetry: agents-playground-server/getConfig {"cleanProperties":{"internalConfig":"{\"locale\":\"en-US\",\"localTimezone\":\"America/Los_Angeles\",\"channelId\":\"msteams\"}"}}

   Telemetry: agents-playground-server/sendActivity {"cleanProperties":{"activityType":"installationUpdate","conversationId":"5305bb42-59c9-4a4c-a2b6-e7a8f4162ede","headers":"{\"x-ms-agents-playground\":\"true\"}"}}

   Telemetry: agents-playground-server/sendActivity {"cleanProperties":{"activityType":"conversationUpdate","conversationId":"5305bb42-59c9-4a4c-a2b6-e7a8f4162ede","headers":"{\"x-ms-agents-playground\":\"true\"}"}}
   ```

The `teamsapptester` command opens your default browser and connects to your agent.

![Your agent in the agents playground](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/quickstart-nodejs/microsoft-365-agents-playground.png)

Now you can send any message to see the echo reply, or send the message `/help` to see how that message is routed to the `_help` handler.

This quickstart guides you through creating a [custom engine agent](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent) that replies back with whatever message you send to it.

## Prerequisites

- .NET 8.0 SDK or newer

  - To install the .NET SDK, go to [dotnet.microsoft.com](https://dotnet.microsoft.com/download), and follow the instructions for your operating system.
  - To verify the version, in a terminal window type `dotnet --version`.

- A code editor of your choice. These instructions use [Visual Studio Code](https://code.visualstudio.com/download).

## Initialize the project and install the SDK

Use `dotnet` to create a new web project and install the required dependencies.

1. Open a terminal and create a new folder

   ```cmd
   mkdir echo
   cd echo
   ```

2. Initialize the .NET project

   ```cmd
   dotnet new web
   ```

3. Install the Agents SDK

   ```cmd
   dotnet add package Microsoft.Agents.Hosting.AspNetCore
   ```

4. Open the folder using Visual Studio Code using this command:

   ```cmd
   code .
   ```

## Import the required libraries

In `Program.cs`, replace the existing content and add the following `using` statements to import the SDK packages into your application code:

```csharp
// Program.cs
using Microsoft.Agents.Builder;
using Microsoft.Agents.Builder.App;
using Microsoft.Agents.Builder.State;
using Microsoft.Agents.Core.Models;
using Microsoft.Agents.Hosting.AspNetCore;
using Microsoft.Agents.Storage;
using Microsoft.AspNetCore.Builder;
```

## Implement the EchoAgent as an AgentApplication

In `Program.cs`, after the `using` statements, add the following code to create the `EchoAgent` extending [AgentApplication](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.app.agentapplication), and implement routes to respond to events:

- Conversation Update
- Any other activity

```csharp
public class EchoAgent : AgentApplication
{
   public EchoAgent(AgentApplicationOptions options) : base(options)
   {
      OnConversationUpdate(ConversationUpdateEvents.MembersAdded, WelcomeMessageAsync);
      OnActivity(ActivityTypes.Message, OnMessageAsync, rank: RouteRank.Last);
   }

   private async Task WelcomeMessageAsync(ITurnContext turnContext, ITurnState turnState, CancellationToken cancellationToken)
   {
        foreach (ChannelAccount member in turnContext.Activity.MembersAdded)
        {
            if (member.Id != turnContext.Activity.Recipient.Id)
            {
                await turnContext.SendActivityAsync(MessageFactory.Text("Hello and Welcome!"), cancellationToken);
            }
        }
    }

   private async Task OnMessageAsync(ITurnContext turnContext, ITurnState turnState, CancellationToken cancellationToken)
   {
      await turnContext.SendActivityAsync($"You said: {turnContext.Activity.Text}", cancellationToken: cancellationToken);
   }
}
```

## Set up the web server and register the agent application

In `Program.cs`, after the `using` statements, add the following code to configure the web host, register the agent, and map the `/api/messages` endpoint:

```csharp
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddHttpClient();
builder.AddAgentApplicationOptions();
builder.AddAgent<EchoAgent>();
builder.Services.AddSingleton<IStorage, MemoryStorage>();

var app = builder.Build();

app.MapPost("/api/messages", async (HttpRequest request, HttpResponse response, IAgentHttpAdapter adapter, IAgent agent, CancellationToken cancellationToken) =>
{
    await adapter.ProcessAsync(request, response, agent, cancellationToken);
});

app.Run();
```

## Set the web server to listen in localhost:3978

In `launchSettings.json`, update the `applicationURL` to `http://localhost:3978` so that the app listens on the correct port.

## Run the agent locally in anonymous mode

From your terminal, run this command:

```cmd
dotnet run
```

The terminal should return something like:

```cmd
info: Microsoft.Hosting.Lifetime[14]
      Now listening on: http://localhost:3978
```

## Test the agent locally

1. From another terminal \(to keep the agent running\) install the [Microsoft 365 Agents Playground](https://www.npmjs.com/package/@microsoft/teams-app-test-tool) with the following command:

   ```cmd
   npm install -g @microsoft/teams-app-test-tool
   ```


   Note


   This command uses npm because the Microsoft 365 Agents Playground is distributed as an npm package.


   The terminal should return something like:


   ```cmd
   added 1 package, and audited 130 packages in 1s

   19 packages are looking for funding
   run `npm fund` for details

   found 0 vulnerabilities
   ```

2. Run the test tool to interact with your agent using this command:

   ```cmd
   teamsapptester
   ```


   The terminal should return something like:


   ```cmd
   Telemetry: agents-playground-cli/serverStart {"cleanProperties":{"options":"{\"configFileOptions\":{\"path\":\"<REDACTED: user-file-path>\"},\"appConfig\":{},\"port\":56150,\"disableTelemetry\":false}"}}

   Telemetry: agents-playground-cli/cliStart {"cleanProperties":{"isExec":"false","argv":"<REDACTED: user-file-path>,<REDACTED: user-file-path>"}}

   Listening on 56150
   Microsoft 365 Agents Playground is being launched for you to debug the app: http://localhost:56150
   started web socket client
   started web socket client
   Waiting for connection of endpoint: http://127.0.0.1:3978/api/messages
   waiting for 1 resources: http://127.0.0.1:3978/api/messages
   wait-on(37568) complete
   Telemetry: agents-playground-server/getConfig {"cleanProperties":{"internalConfig":"{\"locale\":\"en-US\",\"localTimezone\":\"America/Los_Angeles\",\"channelId\":\"msteams\"}"}}

   Telemetry: agents-playground-server/sendActivity {"cleanProperties":{"activityType":"installationUpdate","conversationId":"5305bb42-59c9-4a4c-a2b6-e7a8f4162ede","headers":"{\"x-ms-agents-playground\":\"true\"}"}}

   Telemetry: agents-playground-server/sendActivity {"cleanProperties":{"activityType":"conversationUpdate","conversationId":"5305bb42-59c9-4a4c-a2b6-e7a8f4162ede","headers":"{\"x-ms-agents-playground\":\"true\"}"}}
   ```

The `teamsapptester` command opens your default browser and connects to your agent.

![Your agent in the agents playground](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/media/quickstart-nodejs/microsoft-365-agents-playground.png)

In the text input, enter and send any message to see the echo reply.

## Next steps

- [Check out Agents SDK samples on GitHub](https://github.com/microsoft/Agents/tree/main/samples)
- [Learn more about the Activity protocol and working with activities](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/activity-protocol)
- [Review the AgentApplication events you can respond to from the client](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.app.agentapplication#methods)
- [Review the TurnContext events you can sent back to the client](https://learn.microsoft.com/en-us/dotnet/api/microsoft.agents.builder.turncontext#methods)
- [Provision Azure resources to use with Agents SDK](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/provision-azure-bot-service-manually)
- [Configure your .NET Agent to use OAuth](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/agent-oauth-configuration-dotnet)

The Agents Playground is available by default if you're already using the Microsoft 365 Agents Toolkit. You can use one of the following guides if you want to get started with the toolkit:

- [Create .NET agents in Visual Studio using the Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/create-new-toolkit-project-vs)
- [Create JavaScript agents in Visual Studio Code with the Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/create-new-toolkit-project-vsc)
