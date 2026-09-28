<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-python -->
<!-- Sitemap-Last-Modified: 2026-02-19 -->

# Azure Bot Framework SDK to Microsoft 365 Agents SDK migration guidance for Python

This article describes the required changes to migrate from the Bot Framework SDK for Python to the Microsoft 365 Agents SDK for Python.

Tip

Treat this work as a modernization effort, not only a package swap. The Agents SDK favors simpler, unopinionated patterns \(async/await, dependency injection, standard logging\) and removes legacy features. Keep only what your bot actually needs and avoid carrying forward old template complexity.

## Prerequisites

- [Python](https://www.python.org/) version 3.10 or higher \(3.11+ recommended, supports up to 3.14\)
- Existing Bot Framework SDK project
- Azure Bot Service resource

## Azure resources

Your existing Azure resources remain unchanged during this migration. Continue using your current Azure Bot registration \(App ID and secret\). You reference those values in the new configuration structure described later. Many solutions also include legacy app settings such as `APP_ID`, `APP_PASSWORD`, and `APP_TENANT_ID`. These entries are harmless during migration but the Microsoft 365 Agents SDK no longer uses them. You can remove these settings after you validate the new configuration.

## First steps

Start by updating package dependencies. The following changes don't cover every namespace you might need to touch, but they handle most package substitutions.

### Update package dependencies

| Bot Framework SDK | Agents SDK |
| --- | --- |
| `botbuilder-core` | [`microsoft-agents-hosting-core`](https://pypi.org/project/microsoft-agents-hosting-core/) |
| `botbuilder-schema` | [`microsoft-agents-activity`](https://pypi.org/project/microsoft-agents-activity/) |
| `botbuilder-azure` | [`microsoft-agents-storage-blob`](https://pypi.org/project/microsoft-agents-storage-blob/) and [`microsoft-agents-storage-cosmos`](https://pypi.org/project/microsoft-agents-storage-cosmos/) |
| `botbuilder-integration-aiohttp` | [`microsoft-agents-hosting-aiohttp`](https://pypi.org/project/microsoft-agents-hosting-aiohttp/) |

If your bot integrates with Microsoft Teams, include the Teams Extension package [`microsoft-agents-hosting-teams`](https://pypi.org/project/microsoft-agents-hosting-teams/) for core Teams features.

For authentication, add [`microsoft-agents-authentication-msal`](https://pypi.org/project/microsoft-agents-authentication-msal/) to handle MSAL-based authentication.

Update your `requirements.txt` or equivalent dependency file to replace Bot Framework packages with their Agents SDK equivalents. Use `pip install -r requirements.txt` or your preferred package manager to install the new dependencies.

The Agents SDK enforces code quality standards by using `black` for formatting and `flake8` for linting. Consider adding these tools to your development dependencies.

### Update imports

Important

The Agents SDK uses underscores in import paths \(`microsoft_agents`\) instead of dots \(`microsoft.agents`\). This change affects all imports.

Next, update imports. The easiest approach is a project-wide find-and-replace of the exact text.

| Bot Framework Import | Agents SDK Import |
| --- | --- |
| `from botbuilder.core import ...` | `from microsoft_agents.hosting.core import ...` |
| `from botbuilder.schema import ...` | `from microsoft_agents.activity import ...` |
| `from botbuilder.integration.aiohttp import ...` | `from microsoft_agents.hosting.aiohttp import ...` |
| `from botbuilder.core.teams import ...` | `from microsoft_agents.hosting.teams import ...` |

### Type and class renames

Some types and classes have different names in the Agents SDK. Use the following mappings to guide your changes.

| Bot Framework | Agents SDK |
| --- | --- |
| `BotState` | `AgentState` |
| `BotFrameworkAdapter` | `CloudAdapter` |
| `BotFrameworkHttpClient` | `AgentHttpClient` |
| `OAuthPromptSettings.connection_name` | `OAuthPromptSettings.azure_bot_oauth_connection_name` |

### Activity class changes

The [`Activity`](https://github.com/Microsoft/Agents-for-python/blob/main/packages/activity/microsoft_agents/activity/activity.py) class in the Agents SDK includes built-in validation by using [Pydantic](https://docs.pydantic.dev/). You can parse and validate activities from JSON or dictionaries by using `Activity.model_validate()`.

Additionally, the `Activity` class centralizes operations related to activity payloads. Methods that were previously static methods on `TurnContext` are now instance methods on `Activity`:

| Bot Framework Static Method | Agents SDK Instance Method |
| --- | --- |
| `TurnContext.apply_conversation_reference()` | `activity.apply_conversation_reference()` |
| `TurnContext.get_conversation_reference()` | `activity.get_conversation_reference()` |
| `TurnContext.get_reply_conversation_reference()` | `activity.get_reply_conversation_reference()` |
| `TurnContext.remove_recipient_mention()` | `activity.remove_recipient_mention()` |
| `TurnContext.get_mentions()` | `activity.get_mentions()` |
| `TurnContext.remove_mention_text()` | `activity.remove_mention_text()` |

Update common `turn_state` references. Replace the following usages accordingly.

| Bot Framework | Agents SDK |
| --- | --- |
| `turn_context.turn_state.get(ConnectorClient)` | `turn_context.services.get(ConnectorClient)` |
| `turn_context.turn_state.get(UserTokenClient)` | `turn_context.services.get(UserTokenClient)` |
| `turn_context.turn_state` | `turn_context.services` |

## Configuration

The Agents SDK uses environment variables with a hierarchical naming convention for configuration.

### Environment variables

Create or update your `.env` file with the following structure:

```env
# Required for Azure Bot Service
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID=your-app-id
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTSECRET=your-app-secret
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__TENANTID=your-tenant-id

# Optional - for local debugging
PORT=3978
```

**Migration Note**: Update your environment variable names as shown in the following table:

| Bot Framework SDK | Agents SDK |
| --- | --- |
| `APP_ID` or `MICROSOFT_APP_ID` | `CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTID` |
| `APP_PASSWORD` or `MICROSOFT_APP_PASSWORD` | `CONNECTIONS__SERVICE_CONNECTION__SETTINGS__CLIENTSECRET` |
| `APP_TENANT_ID` or `MICROSOFT_APP_TENANT_ID` | `CONNECTIONS__SERVICE_CONNECTION__SETTINGS__TENANTID` |

The Agents SDK configuration uses double underscores \(`__`\) to represent nested configuration hierarchies. This pattern allows for flexible configuration management across different deployment environments.

## Startup and initialization

Initialization differs in the Agents SDK. The Bot Framework SDK typically used `aiohttp` with manual adapter configuration. By using the Agents SDK, you can use the built-in server utilities for simplified setup.

### Server setup

#### Bot Framework SDK approach

```python
from aiohttp import web
from botbuilder.core import BotFrameworkAdapter, BotFrameworkAdapterSettings
from botbuilder.schema import Activity

# Configure adapter
SETTINGS = BotFrameworkAdapterSettings(
    app_id=os.environ.get("APP_ID", ""),
    app_password=os.environ.get("APP_PASSWORD", "")
)
ADAPTER = BotFrameworkAdapter(SETTINGS)

# Bot instance
BOT = MyBot()

async def messages(req: web.Request) -> web.Response:
    if "application/json" in req.headers["Content-Type"]:
        body = await req.json()
    else:
        return web.Response(status=415)

    activity = Activity().deserialize(body)
    auth_header = req.headers["Authorization"] if "Authorization" in req.headers else ""

    response = await ADAPTER.process_activity(activity, auth_header, BOT.on_turn)
    if response:
        return web.json_response(data=response.body, status=response.status)
    return web.Response(status=201)

APP = web.Application()
APP.router.add_post("/api/messages", messages)

if __name__ == "__main__":
    web.run_app(APP, host="localhost", port=3978)
```

#### Agents SDK approach \(decorator pattern\)

The recommended approach uses the `AgentApplication` with decorators for a more modern, declarative style:

```python
import re
from os import environ
from dotenv import load_dotenv

from microsoft_agents.hosting.aiohttp import CloudAdapter
from microsoft_agents.hosting.core import (
    Authorization,
    AgentApplication,
    TurnState,
    TurnContext,
    MemoryStorage,
)
from microsoft_agents.authentication.msal import MsalConnectionManager
from microsoft_agents.activity import load_configuration_from_env

# Load environment variables
load_dotenv()
agents_sdk_config = load_configuration_from_env(environ)

# Initialize core components
STORAGE = MemoryStorage()
CONNECTION_MANAGER = MsalConnectionManager(**agents_sdk_config)
ADAPTER = CloudAdapter(connection_manager=CONNECTION_MANAGER)
AUTHORIZATION = Authorization(STORAGE, CONNECTION_MANAGER, **agents_sdk_config)

# Create agent application
AGENT_APP = AgentApplication[TurnState](
    storage=STORAGE,
    adapter=ADAPTER,
    authorization=AUTHORIZATION,
    **agents_sdk_config
)

# Register handlers using decorators
@AGENT_APP.conversation_update("membersAdded")
async def on_members_added(context: TurnContext, _state: TurnState):
    await context.send_activity("Welcome!")
    return True

@AGENT_APP.activity("message")
async def on_message(context: TurnContext, _state: TurnState):
    await context.send_activity(f"You said: {context.activity.text}")
```

The Agents SDK provides `load_configuration_from_env()` to automatically load configuration from environment variables, eliminating manual configuration parsing. The decorator pattern allows you to register handlers declaratively without explicit class-based inheritance.

### Authentication and security

The Bot Framework SDK included JSON Web Token \(JWT\) validation in the adapter. The Agents SDK separates authentication concerns, so you can configure authentication middleware explicitly.

For production environments, ensure JWT validation is enabled through the `CloudAdapter` configuration. The adapter automatically validates incoming requests by using the MSAL authentication configuration.

For local development with the Bot Framework Emulator, you can use empty credentials in your .env file:

```python
# Only for local development with Emulator
CONNECTIONS__SERVICE_CONNECTION__SETTINGS__ANONYMOUS_ALLOWED=True
```

## Activity handling

Most bots created with the Bot Framework SDK are based on the `ActivityHandler` base class.

The Agents SDK provides a compatible `ActivityHandler` that maintains a similar API surface for easier migration.

### Key differences

#### Handler method signature changes

Bot Framework SDK handlers typically use positional parameters, while Agents SDK handlers maintain the same pattern with `TurnContext` as the primary parameter.

#### Additional methods in Agents SDK

| Method | Description |
| --- | --- |
| `on_message_delete()` | Handles message deletion activities |
| `on_message_update()` | Handles message update activities |
| `on_sign_in_invoke()` | Handles sign-in invoke activities |

#### Missing methods in Agents SDK

| Method | Reason |
| --- | --- |
| `on_command_activity()` | Command activities aren't supported |
| `on_command_result_activity()` | Command result activities aren't supported |

### Migration example

#### Bot Framework SDK

```python
from botbuilder.core import ActivityHandler, TurnContext
from botbuilder.schema import ChannelAccount

class MyBot(ActivityHandler):
    async def on_message_activity(self, turn_context: TurnContext):
        await turn_context.send_activity(f"You said: {turn_context.activity.text}")

    async def on_members_added_activity(
        self,
        members_added: list[ChannelAccount],
        turn_context: TurnContext
    ):
        for member in members_added:
            if member.id != turn_context.activity.recipient.id:
                await turn_context.send_activity("Welcome!")
```

#### Agents SDK

```python
from microsoft_agents.hosting.core import AgentApplication, TurnState, TurnContext

# AGENT_APP is initialized as shown in the Startup and initialization section

@AGENT_APP.activity("message")
async def on_message(context: TurnContext, _state: TurnState):
    await context.send_activity(f"You said: {context.activity.text}")

@AGENT_APP.conversation_update("membersAdded")
async def on_members_added(context: TurnContext, _state: TurnState):
    for member in context.activity.members_added:
        if member.id != context.activity.recipient.id:
            await context.send_activity("Welcome!")
    return True
```

The migration is mostly straightforward, with the main changes being the import statements. Most existing `ActivityHandler`-based bots work with minimal modifications.

## State management

`ConversationState`, `UserState`, and `PrivateConversationState` are compatible with a few differences. The core state management patterns are similar to the Bot Framework SDK.

You must register state objects and explicitly save them after modifications.

```python
from microsoft_agents.hosting.core import (
    AgentApplication,
    TurnState,
    TurnContext,
    ConversationState,
    UserState,
    MemoryStorage,
)

# Initialize storage and state
STORAGE = MemoryStorage()
conversation_state = ConversationState(STORAGE)
user_state = UserState(STORAGE)
count_property = conversation_state.create_property("conversation_data")

# AGENT_APP is initialized as shown in the Startup and initialization section

@AGENT_APP.activity("message")
async def on_message(context: TurnContext, _state: TurnState):
    # Access state
    conversation_data = await count_property.get(context, {})

    # Modify state
    conversation_data["count"] = conversation_data.get("count", 0) + 1
    await count_property.set(context, conversation_data)

    await context.send_activity(f"Message count: {conversation_data['count']}")

    # Save state changes
    await conversation_state.save_changes(context)
    await user_state.save_changes(context)
```

### Storage options

The Agents SDK provides storage implementations for different backends:

```python
# Memory storage (development only)
from microsoft_agents.hosting.core import MemoryStorage
storage = MemoryStorage()

# Azure Blob Storage
from microsoft_agents.storage.blob import BlobStorage
storage = BlobStorage(
    connection_string="your-connection-string",
    container_name="bot-state"
)

# Azure Cosmos DB
from microsoft_agents.storage.cosmos import CosmosDbPartitionedStorage
storage = CosmosDbPartitionedStorage(
    cosmos_client_options={
        "url": "your-cosmos-url",
        "key": "your-cosmos-key"
    },
    database_id="bot-db",
    container_id="bot-state"
)
```

## Logging

The Agents SDK uses Python's standard `logging` module. Configure logging in your main application file:

```python
import logging

# Configure logging for Agents SDK
ms_agents_logger = logging.getLogger("microsoft_agents")
console_handler = logging.StreamHandler()
console_handler.setFormatter(
    logging.Formatter("%(asctime)s - %(name)s - %(levelname)s - %(message)s")
)
ms_agents_logger.addHandler(console_handler)
ms_agents_logger.setLevel(logging.INFO)
```

### Log levels

- **DEBUG**: Verbose local state tracking
- **INFO**: Activity handling, API calls, and requests to or from external entities
- **WARNING**: Unexpected events that cause potential problems
- **ERROR**: Observed errors, whether caught or uncaught

## Common migration patterns

### Simple echo bot

#### Simple echo bot in Bot Framework SDK

```python
from botbuilder.core import ActivityHandler, TurnContext

class EchoBot(ActivityHandler):
    async def on_message_activity(self, turn_context: TurnContext):
        await turn_context.send_activity(f"Echo: {turn_context.activity.text}")
```

#### Simple echo bot in Agents SDK

```python
from microsoft_agents.hosting.core import AgentApplication, TurnState, TurnContext

# AGENT_APP is initialized as shown in the Startup and initialization section

@AGENT_APP.activity("message")
async def on_message(context: TurnContext, _state: TurnState):
    await context.send_activity(f"Echo: {context.activity.text}")
```

### State management with counter

```python
from microsoft_agents.hosting.core import (
    AgentApplication,
    TurnState,
    TurnContext,
    ConversationState,
    MemoryStorage,
)

# Initialize storage and state
STORAGE = MemoryStorage()
conversation_state = ConversationState(STORAGE)
count_property = conversation_state.create_property("count")

# AGENT_APP is initialized as shown in the Startup and initialization section

@AGENT_APP.activity("message")
async def on_message(context: TurnContext, _state: TurnState):
    count = await count_property.get(context, 0)
    count += 1
    await count_property.set(context, count)

    await context.send_activity(f"Message count: {count}")
    await conversation_state.save_changes(context)
```

### Teams bot

```python
from microsoft_agents.hosting.core import AgentApplication, TurnState, TurnContext

# AGENT_APP is initialized as shown in the Startup and initialization section
# Include microsoft-agents-hosting-teams in your dependencies for Teams support

@AGENT_APP.conversation_update("membersAdded")
async def on_members_added(context: TurnContext, _state: TurnState):
    for member in context.activity.members_added:
        await context.send_activity(f"Welcome to the team, {member.name}!")
    return True

@AGENT_APP.activity("message")
async def on_message(context: TurnContext, _state: TurnState):
    # Remove mentions
    text = context.activity.remove_mention_text(context.activity.recipient.id)
    await context.send_activity(f"You said: {text}")
```

## Troubleshooting and tips

The following tips might help you be more successful.

### Import errors

If you encounter import errors, ensure you're using underscores \(`microsoft_agents`\) instead of dots \(`microsoft.agents`\) in all import statements. This error is the most common migration problem.

### Async/await patterns

All bot methods must be `async` and use `await` for asynchronous operations. Ensure all calls to `send_activity`, state operations, and dialog operations use `await`.

### Type hints

The Agents SDK uses Python type hints extensively. Consider adding type hints to your bot code for better IDE support and error detection:

```python
from microsoft_agents.hosting.core import TurnContext

async def on_message_activity(self, turn_context: TurnContext) -> None:
    await turn_context.send_activity("Hello")
```

### Configuration validation

If your bot fails to start due to configuration errors, verify your environment variable names use the correct double-underscore \(`__`\) notation and that you set all required values.

### Local 401 errors during debugging

If you see 401 errors during local debugging by using the Bot Framework Emulator, verify your credentials are correctly configured in the `.env` file or use the Emulator's authentication settings.

### Python version compatibility

Ensure you're using Python 3.10 or higher. The Agents SDK uses modern Python features that aren't available in earlier versions.

## Migration checklist

✓ **Analyze and plan**: Identify any deprecated features and decide migration vs. rebuild scope. ✓ **Upgrade Python version**: Move to Python 3.10 or higher \(3.11+ recommended\). ✓ **Replace packages**: Remove `botbuilder-*`; add `microsoft-agents-*` \(hosting-core, activity, hosting-aiohttp, authentication-msal, storage providers, hosting-teams\). ✓ **Update imports**: Apply find/replace per the tables above; change all `microsoft.agents` to `microsoft_agents`. ✓ **Update types and classes**: Fix renamed APIs and move `TurnContext` static methods to `Activity` instance methods. ✓ **Update configuration**: Create `.env` file with hierarchical naming \(double underscores\). ✓ **Update initialization**: Use `CloudAdapter` with `MsalAuth.from_environment()` and `AgentsHttpMiddleware`. ✓ **Configure logging**: Set up Python logging for `microsoft_agents` logger. ✓ **Build and test locally**: Use the Bot Framework Emulator with credentials; validate core scenarios. ✓ **Deploy and monitor**: Update environment variables in Azure to match the new configuration and watch logs after rollout.

## Related content

- [Azure Bot Framework SDK to Agents SDK migration guidance](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-guidance)
- [Azure Bot Framework SDK to Microsoft 365 Agents SDK migration guidance for .NET](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-dotnet)
- [Azure Bot Framework SDK to Microsoft 365 Agents SDK migration guidance for Node.js](https://learn.microsoft.com/en-us/microsoft-365/agents-sdk/bf-migration-nodejs)
